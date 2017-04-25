## Motivace

pro kazde zarizeni zjistit pocet restartu programu

## OLAP varianta
### Pivot table pro restarty programu

(*dimenze*: program_ver, device, year, month, day) (*measure*: pocet restartu)

```sql
CREATE MATERIALIZED VIEW agg_ver_dev AS 
SELECT program_ver, 
       device,                                                     
       DATE_PART('YEAR',t2.time) as year,
       DATE_PART('MONTH',t2.time) as month,
       DATE_PART('DAY', t2.time) as day,
       count(*) as restart_count
FROM (
      SELECT program_ver,                                                                          
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      (
        SELECT car_key,time, coalesce(device,'N/A') as device, app_run_time 
        FROM service_log
      ) t2                                          
      ON t1.car_key = t2.car_key 
         AND t2.time >= session_begin 
         AND t2.time <= session_end 
WHERE app_run_time <= 0.17 
GROUP BY rollup(device,DATE_PART('YEAR',t2.time), DATE_PART('MONTH',t2.time), DATE_PART('DAY',t2.time)),program_ver;
```

### Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017

```sql
SELECT program_ver, device, max(restart_count) as max_restart_count 
FROM agg_ver_dev 
WHERE year=2017 AND month=1 AND day is null 
GROUP BY program_ver, device 
ORDER BY max_restart_count DESC 
LIMIT 1;
```

## normal varianta

### view restartu verzi a typu zarizeni (vsechny restarty, nic neni agregovano)

```sql
CREATE VIEW view_ver_dev AS 
SELECT program_ver, device, t2.time, t2.app_run_time 
FROM (
      SELECT program_ver,                                                                          
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      (SELECT car_key,time, coalesce(device,'N/A') as device, app_run_time FROM service_log) t2                                           
      ON t1.car_key = t2.car_key 
         AND t2.time >= session_begin 
         AND t2.time <= session_end 
WHERE app_run_time <= 0.17;
```

### Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017

```sql
SELECT program_ver, device, count(*) as restart_count
FROM view_ver_dev 
WHERE DATE_PART('YEAR',view_ver_dev.time) = '2017' AND DATE_PART('MONTH',view_ver_dev.time)='1' 
GROUP BY program_ver, device
ORDER BY restart_count DESC
LIMIT 1;
```
