# Day 1 - Oracle DBA Health Check Commands

## 1. Check Database Status

```sql
SELECT name,
       open_mode,
       database_role,
       log_mode
FROM v$database;

## 2. Check Instance Status
SELECT instance_name, status, startup_time, version
FROM v$instance;

## 3. Check Database Role
SELECT name,
       db_unique_name,
       database_role,
       open_mode,
       log_mode
FROM v$database;

## 4. Check Tablespaces
SELECT tablespace_name,
       status,
       contents
FROM dba_tablespaces
ORDER BY tablespace_name;


## 5. Check Datafiles

SELECT tablespace_name,
       file_name,
       bytes/1024/1024 AS size_mb,
       autoextensible
FROM dba_data_files
ORDER BY tablespace_name;

## 6. Check Temporary Files
SELECT tablespace_name,
       file_name,
       bytes/1024/1024 AS size_mb
FROM dba_temp_files;

## 7. Check Users
SELECT username,
       account_status,
       default_tablespace,
       temporary_tablespace
FROM dba_users
ORDER BY username;

## 8. Check Invalid Objects
SELECT owner,
       object_type,
       COUNT(*)
FROM dba_objects
WHERE status = 'INVALID'
GROUP BY owner, object_type
ORDER BY owner, object_type;

## 9. Check Oracle Components

SELECT comp_name,
       version,
       status
FROM dba_registry;

## 10. Check Diagnostic Information
SELECT name,
       value
FROM v$diag_info;

## 11. Check SPFILE
SHOW PARAMETER spfile;

## 12. Check Important Parameters
Processes

SHOW PARAMETER processes;

Sessions

SHOW PARAMETER sessions;


Memory

SHOW PARAMETER memory;

Diagnostic Destination

SHOW PARAMETER diagnostic_dest;

