# mysql_sys.x-schema_tables_with_full_table_scans-

SELECT 
    `performance_schema`.`table_io_waits_summary_by_index_usage`.`OBJECT_SCHEMA` AS `object_schema`,
    `performance_schema`.`table_io_waits_summary_by_index_usage`.`OBJECT_NAME` AS `object_name`,
    `performance_schema`.`table_io_waits_summary_by_index_usage`.`COUNT_READ` AS `rows_full_scanned`,
    `performance_schema`.`table_io_waits_summary_by_index_usage`.`SUM_TIMER_WAIT` AS `latency`
FROM
    `performance_schema`.`table_io_waits_summary_by_index_usage`
WHERE
    ((`performance_schema`.`table_io_waits_summary_by_index_usage`.`INDEX_NAME` IS NULL)
        AND (`performance_schema`.`table_io_waits_summary_by_index_usage`.`COUNT_READ` > 0))
ORDER BY `performance_schema`.`table_io_waits_summary_by_index_usage`.`COUNT_READ` DESC
