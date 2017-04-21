## Motivace
zjistit pro kazdou verzi typ zarizeni, ktery se nejcasteji restartoval

## OLAP varianta
### Pivot table

```sql
CREATE MATERIALIZED VIEW agg_device_ver_restarts AS 
SELECT program_ver, 
       device,
       DATE_PART('YEAR',service_log.time) as year,
       DATE_PART('MONTH',service_log.time) as month,
       DATE_PART('DAY',service_log.time) as day,
       count(*) as restart_count
FROM (
      SELECT pda_imei, program_ver,
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
          program_ver, device
;
```

### Zjistit pro kazdou verzi programu typ zarizeni, ktery se nejcasteji restartoval

```sql
SELECT program_ver, device, restart_count
FROM (
        SELECT program_ver, device, restart_count, max(restart_count) OVER (PARTITION BY program_ver)  
        FROM agg_device_ver_restarts 
        WHERE year is null AND month is null AND day is null
     ) t 
WHERE max = restart_count;
```
