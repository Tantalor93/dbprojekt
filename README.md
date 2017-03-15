#Projekt z db systémů
===

• conn_log(log_key, sim_imsi, time, car_key, pda_imei, gsmnet_id, method, program_ver)
- log_key (int): primární klíč, nemá další význam, klasický auto_increment
- sim_imsi (int): identifikátor SIM karty
- time (datetime): čas
- car_key (int): identifikátor auta
- pda_imei (int): identifikátor PDA
- gsmnet_id (int): identifikátor sítě, prefix 230 znamená "cz"
- method (int): UDP / TCP
- program_ver (string): verze programu

Vzniká zde záznam po každém připojení zařízení
-- občas tam chybí záznamy o gsmnet_id / pda_imei... čudné

• service_log(service_key, car_key, time, app_run_time, pda_run_time, device)
- service_key (int): primární klíč, nemá další význam (v datech jsou díry neví někdo proč?)
- car_key (int): stejné jako conn_log.car_key
- time (datetime): čas vytvoření záznamu
- app_run_time (float): počet hodin po které je appka zapnutá
- pda_run_time (float): počet hodin po které je zařízení zapnutné
- device (string): typ zařízení

Do té tabulky se dávají pouze inserty, periodicky každých X minut ("furt běžím, furt běžím...")
-- Nevidím tam žádný identifikátor kromě `car_key`, takže se to bude asi muset podle toho (asi nemůžeš mít dvě PDA v jednom autě)

**restore backupu**:

`
 psql -h db.fi.muni.cz pgdb xbenkov1 < db-95-conn.backup
 `

**pripojeni k serveru**:

`
psql -h db.fi.muni.cz pgdb xbenkov1
`

**pro kazdou verzi programu zjistit pocty ruznych zarizeni**:

 ```sql
SELECT program_ver, COUNT(DISTINCT(pda_imei))
FROM conn_log
GROUP BY program_ver;
 ```

**pro kazde zarizeni zjistit pocet restartu programu**:

```sql
SELECT pda_imei, COUNT(service_log.app_run_time)
FROM (
      SELECT pda_imei ,car_key, min, lead(min,1,now()) OVER (partition by car_key ORDER BY min)
      FROM (
            SELECT  pda_imei, car_key, min(time)
            FROM conn_log
            GROUP BY pda_imei, car_key
            ) t
     ) t1
INNER JOIN service_log ON t1.car_key = service_log.car_key
                                AND service_log.time >= t1.min AND service_log.time <= lead
WHERE app_run_time <= 0.17
GROUP BY pda_imei;
```

**pro kazdou verzi programu zjistit pocet restartu jeho programu**:

```sql
SELECT program_ver, COUNT(service_log.app_run_time) 
FROM (
      SELECT program_ver, car_key, min, lead(min,1,now()) OVER (partition by car_key ORDER BY min) 
      FROM (
            SELECT program_ver, car_key, min(time) 
            FROM conn_log 
            GROUP BY program_ver, car_key
            ) t
     ) t1 
INNER JOIN service_log ON t1.car_key = service_log.car_key 
                                AND service_log.time >= t1.min AND service_log.time <= lead 
WHERE app_run_time <= 0.17 
GROUP BY program_ver;
```

**pro kazdou verzi programu zjistit nejdelší běh zařízení**:
```sql
SELECT program_ver, max(service_log.pda_run_time)
FROM (
      SELECT program_ver, car_key, min, lead(min,1,now()) OVER (partition by car_key ORDER BY min)
      FROM (
            SELECT  program_ver, car_key, min(time)
            FROM conn_log
            GROUP BY program_ver, car_key
            ) t
     ) t1
INNER JOIN service_log ON t1.car_key = service_log.car_key
                                AND service_log.time >= t1.min AND service_log.time <= lead
GROUP BY program_ver;
```

 **pro kazde zarizeni zjistit, kdy bylo uvedeno do provozu**:

```sql
SELECT pda_imei, min(time)
FROM conn_log
GROUP BY pda_imei;
```

**pro kazde auto, zjistit pocet ruznych zarizeni**:

```sql
SELECT car_key, count(distinct(pda_imei))
FROM conn_log 
GROUP BY car_key;
```

**pro kazdy typ zarizeni, zjistit pocet restartu aplikace**:

```sql
SELECT device, COUNT(app_run_time) 
FROM service_log 
WHERE app_run_time <= 0.17 
GROUP BY device;
```

query, ktery zahrne i pocet restartu pro vsechny zarizeni (OLAP varianta)

```sql
SELECT t.device, COUNT(app_run_time) 
FROM (
      SELECT coalesce(device,'N/A') AS device, app_run_time 
      FROM service_log
      ) t 
WHERE app_run_time <= 0.17 
GROUP BY rollup(device);
```

query, ktery zahrne i pocet restartu pro vsechny zarizeni

```sql
SELECT coalesce(device,'N/A') AS device, COUNT(app_run_time) 
FROM service_log 
WHERE app_run_time <= 0.17 
GROUP BY device 
UNION 
SELECT null as device, COUNT(*) 
FROM service_log 
WHERE app_run_time <= 0.17;
```

**pro kazdy typ zarizeni, zjistit nejdelsi a prumerny beh zarizeni**:

```sql
SELECT device, max(pda_run_time), avg(pda_run_time) 
FROM service_log 
GROUP BY device;
```

**kolik bylo vytvoreno spojeni dle roku, mesice a dne**:

OLAP verze

```sql
SELECT DATE_PART('YEAR',time) AS year,
       DATE_PART('MONTH',time) AS month,
       DATE_PART('DAY',time) AS day,
       count(*) AS number_of_connections
FROM conn_log 
GROUP BY ROLLUP (DATE_PART('YEAR', time), DATE_PART('MONTH', time), DATE_PART('DAY', time));
```

NO OLAP verze

```sql
SELECT DATE_PART('YEAR', time) AS year,
       DATE_PART('MONTH', time) AS month,
       DATE_PART('DAY', time) AS day,
       count(*) AS number_of_connections
FROM conn_log 
GROUP BY DATE_PART('YEAR', time), DATE_PART('MONTH', time), DATE_PART('DAY', time) 
UNION 
SELECT null, null, null, count(*) AS number_of_connections 
FROM conn_log 
UNION 
SELECT DATE_PART('YEAR', time), null, null, count(*) 
FROM conn_log 
GROUP BY DATE_PART('YEAR', time) 
UNION 
SELECT DATE_PART('YEAR', time), DATE_PART('MONTH', time), null, count(*)
FROM conn_log 
GROUP BY DATE_PART('YEAR', time), DATE_PART('MONTH', time);
```

**kolik unikatnich zarizeni vytvorilo spojeni dle roku, mesice a dne**:

```sql
SELECT DATE_PART('YEAR',time) AS year,
       DATE_PART('MONTH',time) AS month,
       DATE_PART('DAY',time) AS day,
       count(distinct(pda_imei)) AS number_of_connections
FROM (
      SELECT coalesce(pda_imei,'N/A') as pda_imei, time 
      FROM conn_log
      ) t   
GROUP BY ROLLUP (DATE_PART('YEAR', time), DATE_PART('MONTH', time), DATE_PART('DAY', time));
```

**pro kazdou verzi zjisti kolik spojeni bylo vytvoreno danym protokolem a kolik bylo celkem spojeni a kolik spojeni bylo pro dany protokol nehlede na verzi**:

OLAP verze
```sql
SELECT program_ver,method,count(*) 
FROM conn_log 
GROUP BY GROUPING SETS((program_ver,method),(method),());
```

normal verze

```sql
SELECT program_ver,method,count(*) 
FROM conn_log 
GROUP BY program_ver,method 
UNION 
SELECT null, method, count(*) 
FROM conn_log 
GROUP BY method 
UNION SELECT null, null, count(*) 
FROM conn_log;
```

**zjisteni bezicich dotazu**:

```sql
select * from pg_stat_activity where usename = 'xbenkov1';
```

**pustit soubor s SQL jako background task**:

ale predtim se jeste musi nahrat do env property `PGPASSWORD` heslo k DB userovi

`
export PGPASSWORD=HESLO;
`

`
nohup psql -h db.fi.muni.cz pgdb xbenkov1 -f p.sql > result2.log 2>&1 &
`

vysledek dotazu ze souboru p.sql je v souboru result2.log

**analyza dotazu (napr. jak dlouho bezel)**

```sql
EXPLAIN ANALYSE
SELECT COUNT(DISTINCT(pda_imei)), program_ver
FROM xbenkov1.conn_log
GROUP BY program_ver;
```

**Ukazka vytvoreni materialized view**:

```sql
CREATE MATERIALIZED VIEW number_of_restarts AS SELECT pda_imei, COUNT(app_run_time)
FROM public.conn_log
INNER JOIN public.service_log ON public.conn_log.car_key = public.service_log.car_key
WHERE app_run_time >= 0
  AND app_run_time < 0.17 GROUP BY pda_imei;
```

**data ve vytvorenem view lze obnovit pomoci**:

```sql
REFRESH MATERIALIZED VIEW number_of_restarts;
```

**vysledky z mat. view se ziskavaji klasicky selectem**:

```sql
SELECT * FROM number_of_restarts;
```

**jednoduche pozorovani casu**:
puvodni select: ~1min
vytvoreni mat. view: ~1min
refresh: ~1min
select z mat. view: ~700ms

**do materialized view nelze insertovat**
