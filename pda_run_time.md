## Motivace 
pro kazde zarizeni zjistit kolik hodin bylo pouzivano

## OLAP varianta
### Pivot table

(*dimenze*: pda_imei, year, month, day) (*measure*: doba behu v hodinach)

```sql
CREATE MATERIALIZED VIEW pda_run_time AS 
SELECT pda_imei, 
       DATE_PART('YEAR',t2.time) as year,
       DATE_PART('MONTH',t2.time) as month,
       DATE_PART('DAY',t2.time) as day,
       sum(t2.pda_run_time) 
FROM (
      SELECT pda_imei,
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      (
       SELECT *
       FROM (
             SELECT car_key,
                    pda_run_time, 
                    time,
                    lead(pda_run_time,1,0.17) OVER (Partition by car_key ORDER BY time) AS next_pda_run_time 
             FROM service_log) t 
       WHERE next_pda_run_time <= 0.17
      ) t2
      ON t1.car_key = t2.car_key 
         AND t2.time >= session_begin 
         AND t2.time <= session_end 
GROUP BY pda_imei, rollup(DATE_PART('YEAR',t2.time),DATE_PART('MONTH',t2.time),DATE_PART('DAY',t2.time));
```

### pro kazde zarizeni zjistit kolik hodin bylo pouzivano

```sql
SELECT pda_imei, sum  
FROM pda_run_time 
WHERE year is null AND month is null AND day is null;
```

## normal varianta

### pro kazde zarizeni zjistit kolik hodin bylo pouzivano

```sql
SELECT pda_imei, 
       sum(t2.pda_run_time) 
FROM (
      SELECT pda_imei,
             car_key,
             time as session_begin,
             lead(time,1,now()) OVER (Partition by car_key ORDER BY time) AS session_end 
      FROM conn_log
      ) t1 
      INNER JOIN 
      (
       SELECT *
       FROM (
             SELECT car_key,
                    pda_run_time, 
                    time,
                    lead(pda_run_time,1,0.17) OVER (Partition by car_key ORDER BY time) AS next_pda_run_time 
             FROM service_log) t 
       WHERE next_pda_run_time <= 0.17
      ) t2
      ON t1.car_key = t2.car_key 
         AND t2.time >= session_begin 
         AND t2.time <= session_end 
GROUP BY pda_imei;
```
