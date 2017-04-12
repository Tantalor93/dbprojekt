## Motivace 
pro kazdou verzi programu zjistit pocty ruznych zarizeni

## Olap verze

### Pivot table

(*dimenze*: program_ver, year, month, day) (*measure*: pocet ruznych zarizeni)

```sql
CREATE MATERIALIZED VIEW agg_ver_pda AS 
SELECT program_ver,
       DATE_PART('YEAR',time) as year,
       DATE_PART('MONTH',time) as month,
       DATE_PART('DAY',time) as day,
       COUNT(DISTINCT(pda_imei))
FROM conn_log
GROUP BY program_ver, rollup(DATE_PART('YEAR',time),DATE_PART('MONTH',time),DATE_PART('DAY',time));
```

### Celkovy pocet ruznych zarizeni pro kazdou verzi

```sql
SELECT program_ver, count 
FROM agg_ver_pda 
WHERE year is null AND month is null AND day is null;
```

## Normal verze

### Celkovy pocet ruznych zarizeni pro kazdou verzi

```sql
SELECT program_ver, COUNT(DISTINCT(pda_imei))                                                   
FROM conn_log
GROUP BY program_ver;
```
