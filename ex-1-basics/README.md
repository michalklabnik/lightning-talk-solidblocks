# Ex. 1 Basics

## Start

```shell
dc up
# Logs + data dirs
```

## Login

```shell
dc exec -e PGPASSWORD=rdspassword1 pg14 psql -h 127.0.0.1 -U rds postgres
```

```shell
dc exec -e PGPASSWORD=password1 pg14 psql -h 127.0.0.1 -U user1 database1
```

```shell
# Logged user
\c
# List databases
\l
```

## Parameters

```shell
SELECT name, setting, unit, boot_val
FROM pg_settings
WHERE name IN ('max_connections', 'wal_buffers', 'work_mem');
```

## Extensions

```shell
# List extensions
\dx
# List available extensions
SELECT * FROM pg_available_extensions;
```

```shell
dc exec pg14 /rds/bin/backup-info.sh

dc exec pg14 /rds/bin/backup-full.sh
dc exec pg14 /rds/bin/backup-incr.sh
dc exec pg14 /rds/bin/backup-diff.sh
```

## Upgrade

```shell
# Update 14 to 15
dc exec -e PGPASSWORD=rdspassword1 pg15 psql -h 127.0.0.1 -U rds postgres -V
# Logs + data dirs
```

```shell
dc exec pg15 /rds/bin/backup-info.sh
dc exec pg15 /rds/bin/backup-full.sh
```
