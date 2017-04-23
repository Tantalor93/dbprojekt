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
WHERE DATE_PART('YEAR',time)=2017 AND DATE_PART('MONTH',time)=1
GROUP BY program_ver;
```

## Normalni verze s indexy 

aby indexy fungovali i nad vyrazy DATE_PART je potreba zavest nove fce, ktere budeme moci cachovat a pote i indexovat

### pomocne fce

```sql
CREATE FUNCTION month_idxable(timestamp with time zone) returns double precision AS 
'SELECT date_part(''MONTH'', time) 
 from conn_log' 
LANGUAGE SQL WITH (iscachable)
```

```sql
 CREATE FUNCTION year_idxable(timestamp with time zone) returns double precision 
 AS 'SELECT
 date_part(''YEAR'', time) from conn_log' LANGUAGE SQL WITH
 (iscachable);
```

### vytvoreni indexu 

```sql
CREATE INDEX year_conn ON conn_log(year_idxable(time));
CREATE INDEX month_conn ON conn_log(month_idxable(time));
```

### Pocet spojeni v lednu 2017

```sql
SELECT program_ver, COUNT(*) as conn_count                                                   
FROM conn_log 
WHERE year_idxable(time)=2017 AND month_idxable(time)=1
GROUP BY program_ver;
```

