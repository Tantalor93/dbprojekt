Projekt z db systémů
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

=====================================================
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
 SELECT COUNT(DISTINCT(pda_imei)), program_ver
 FROM xbenkov1.conn_log
 GROUP BY program_ver;
 ```

**pro kazde zarizeni zjistit pocet restartu programu**:

```sql
SELECT pda_imei, COUNT(app_run_time)
FROM xbenkov1.conn_log
INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key
WHERE app_run_time >= 0
  AND app_run_time < 0.17
GROUP BY pda_imei;
```

**pro kazdou verzi programu zjistit pocet restartu jeho programu**:

```sql
SELECT program_ver, COUNT(app_run_time)
FROM xbenkov1.conn_log
INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key
WHERE app_run_time >= 0
  AND app_run_time < 0.17
GROUP BY program_ver;
```

**pro kazdou verzi programu zjistit nejdelší běh zařízení**:
```sql
SELECT program_ver, max(pda_run_time)
FROM xbenkov1.conn_log
INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key
GROUP BY program_ver;
```

**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**:

```sql
SELECT pda_imei, sum(pda_run_time)
FROM xbenkov1.conn_log
INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key
GROUP BY pda_imei;
```

 **pro kazde zarizeni zjistit, kdy bylo uvedeno do provozu**:

```sql
SELECT pda_imei, min(xbenkov1.conn_log.time)
FROM xbenkov1.conn_log
GROUP BY pda_imei;
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

========================================================
**Ukazka vytvoreni materialized view**:

pro kazdou verzi programu zjistit pocet restartu jeho programu:

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
