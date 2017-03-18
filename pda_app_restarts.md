## Motivace

pro kazde zarizeni zjistit pocet restartu programu

## OLAP varianta
### Pivot table pro restarty programu

```sql
CREATE MATERIALIZED VIEW agg_pda_app_restarts AS 
SELECT pda_imei,
       DATE_PART('YEAR',service_log.time) as year,
       DATE_PART('MONTH',service_log.time) as month,
       DATE_PART('DAY',service_log.time) as day,
       count(service_log.app_run_time) 
FROM (
      SELECT pda_imei,
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
GROUP BY rollup(DATE_PART('YEAR',service_log.time),DATE_PART('MONTH',service_log.time),DATE_PART('DAY',service_log.time)),
         pda_imei;
```

### TOP 10 zarizeni, ktere se restartovali v lednu 2017

```sql
SELECT pda_imei, count 
FROM agg_pda_app_restarts 
WHERE year='2017' AND month='1' AND day is null 
ORDER BY count DESC 
LIMIT 10;
```

## normal varianta

### tabulka restartu zarizeni (vsechny restarty vsech zarizeni, nic neni agregovano)

```sql
CREATE MATERIALIZED VIEW pda_app_restarts AS  
SELECT pda_imei, service_log.time, service_log.app_run_time 
FROM (
      SELECT pda_imei,
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

### TOP 10 zarizeni, ktere se restartovali v lednu 2017

```sql
SELECT pda_imei, count(pda_app_restarts.app_run_time) 
FROM pda_app_restarts 
WHERE DATE_PART('YEAR',pda_app_restarts.time) = '2017' AND DATE_PART('MONTH',pda_app_restarts.time)='1' 
GROUP BY pda_imei 
ORDER BY count DESC 
LIMIT 10;
```
