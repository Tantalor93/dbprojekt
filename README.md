restore backupu:
 psql -h db.fi.muni.cz pgdb xbenkov1 < db-95-conn.backup

pripojeni k serveru:
 psql -h db.fi.muni.cz pgdb xbenkov1

pro kazdou verzi programu zjistit pocty ruznych zarizeni:
 SELECT COUNT(DISTINCT(pda_imei)),program_ver FROM xbenkov1.conn_log GROUP BY program_ver;

pro kazde zarizeni zjistit pocet restartu programu:
SELECT pda_imei, COUNT(app_run_time) FROM xbenkov1.conn_log INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key WHERE app_run_time >= 0 AND app_run_time < 1 GROUP BY pda_imei;

pro kazdou verzi programu zjistit pocet restartu jeho programu:
SELECT program_ver, COUNT(app_run_time) FROM xbenkov1.conn_log INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key WHERE app_run_time >= 0 AND app_run_time < 1 GROUP BY program_ver;

pro kazde zarizeni zjistit kolik hodin bylo pouzivano:
SELECT pda_imei, sum(pda_run_time) FROM xbenkov1.conn_log INNER JOIN xbenkov1.service_log ON xbenkov1.conn_log.car_key = xbenkov1.service_log.car_key GROUP BY pda_imei;

bezici dotazy:
select * from pg_stat_activity where usename = 'xbenkov1';

pustit soubor s SQL jako background task:
nohup psql -h db.fi.muni.cz pgdb xbenkov1 -f p.sql > result2.log 2>&1 &
