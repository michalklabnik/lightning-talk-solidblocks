# Ex. 3 CI

## Start

```shell
dc up -d
dc logs -f
```

## Data

```shell
dc exec -e PGPASSWORD=password3 pg14 psql -h 127.0.0.1 -U user3 database3
```

```postgresql
CREATE TABLE app3
(
    key   TEXT NOT NULL,
    value TEXT NOT NULL
);

INSERT INTO app3 (key, value)
VALUES ('msg', 'Hello from CI!');
```

```shell
\dt
SELECT * FROM app3;
```

## Backup

```shell
dc exec pg14 /rds/bin/backup-incr.sh
# Shutdown DB
```

## CI

```shell
rm -r ./postgres_data
```

Manual trigger.
