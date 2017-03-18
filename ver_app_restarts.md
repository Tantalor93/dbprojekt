# OLAP varianta

### Pivot table pro restarty programu

```sql
CREATE MATERIALIZED VIEW agg_ver_app_restarts AS 
SELECT program_ver, 
       DATE_PART('YEAR',service_log.time) as year,
       DATE_PART('MONTH',service_log.time) as month,
       DATE_PART('DAY', service_log.time) as day,
       count(service_log.app_run_time) 
FROM (
      SELECT program_ver,                                                                          
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      service_log                                          
      ON t1.car_key = service_log.car_key 
         AND service_log.time >= session_begin 
         AND service_log.time <= session_end 
WHERE app_run_time <= 0.17 
GROUP BY rollup(DATE_PART('YEAR',service_log.time), DATE_PART('MONTH',service_log.time), DATE_PART('DAY',service_log.time)),program_ver;
```

### Serad verze programu dle toho jak casto se restartovali (od nejmin restartu po nejvic)

```sql
SELECT program_ver, count 
FROM agg_ver_app_restarts
WHERE year='2017' AND month='1' AND day is null 
ORDER BY count ASC;
```

# normal varianta

### tabulka restartu verzi

```sql
CREATE MATERIALIZED VIEW ver_app_restarts AS 
SELECT program_ver, service_log.time, service_log.app_run_time 
FROM (
      SELECT program_ver,                                                                          
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      service_log                                          
      ON t1.car_key = service_log.car_key 
         AND service_log.time >= session_begin 
         AND service_log.time <= session_end 
WHERE app_run_time <= 0.17;
```

### Serad verze programu dle toho jak casto se restartovali (od nejmin restartu po nejvic)

```sql
SELECT program_ver, count(ver_app_restarts.app_run_time) 
FROM ver_app_restarts 
WHERE DATE_PART('YEAR',ver_app_restarts.time) = '2017' AND DATE_PART('MONTH',ver_app_restarts.time)='1' 
GROUP BY program_ver 
ORDER BY count ASC;
```
