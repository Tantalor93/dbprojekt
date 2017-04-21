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
       COUNT(DISTINCT(pda_imei)) as pda_count
FROM conn_log
GROUP BY program_ver, rollup(DATE_PART('YEAR',time),DATE_PART('MONTH',time),DATE_PART('DAY',time));
```

### Celkovy pocet ruznych zarizeni pro kazdou verzi

```sql
SELECT program_ver, pda_count 
FROM agg_ver_pda 
WHERE year is null AND month is null AND day is null;
```

### Pocet ruznych zarizeni v lednu 2017

```sql
SELECT program_ver, pda_count 
FROM agg_ver_pda 
WHERE year=2017 AND month=1 AND day is null;
```

## Normal verze

### Celkovy pocet ruznych zarizeni pro kazdou verzi

```sql
SELECT program_ver, COUNT(DISTINCT(pda_imei)) as pda_count                                                   
FROM conn_log
GROUP BY program_ver;
```

### Pocet ruznych zarizeni v lednu 2017

```sql
SELECT program_ver, COUNT(DISTINCT(pda_imei)) as pda_count                                                   
FROM conn_log 
WHERE DATE_PART('YEAR',time)=2017 AND DATE_PART('MONTH',time)=1
GROUP BY program_ver;
```
