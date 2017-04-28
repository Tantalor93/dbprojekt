## Motivace 
pro kazdou verzi programu zjistit pocet spojeni

## Olap verze

### Pivot table

(*dimenze*: program_ver, year, month, day) (*measure*: pocet restartu)

```sql
CREATE MATERIALIZED VIEW ver_conns AS 
SELECT program_ver,
       DATE_PART('YEAR',time) as year,
       DATE_PART('MONTH',time) as month,
       DATE_PART('DAY',time) as day,
       COUNT(*) as conn_count
FROM conn_log
GROUP BY program_ver, rollup(DATE_PART('YEAR',time),DATE_PART('MONTH',time),DATE_PART('DAY',time));
```

### Pocet spojeni celkem pro kazdou verzi

```sql
SELECT program_ver, conn_count
FROM ver_conns 
WHERE year is null AND month is null AND day is null;
```

### Pocet spojeni v lednu 2017

```sql
SELECT program_ver, conn_count
FROM ver_conns 
WHERE year=2017 AND month=1  AND day is null;
```

## Normalni verze

### Celkovy pocet spojeni pro kazdou verzi

```sql
SELECT program_ver, COUNT(*) as conn_count                                                   
FROM conn_log
GROUP BY program_ver;
```

### Pocet spojeni v lednu 2017

```sql
SELECT program_ver, COUNT(*) as conn_count                                                   
FROM conn_log 
WHERE time >= '2017-01-01' AND time < '2017-02-01'
GROUP BY program_ver;
```
