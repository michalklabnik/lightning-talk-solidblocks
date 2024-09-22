# Ex. 2 Restore

## Start

```shell
dc up -d
dc logs -f
```

## Data

```shell
dc exec -e PGPASSWORD=password2 pg14 psql -h 127.0.0.1 -U user2 database2
```

```postgresql
CREATE TABLE app2
(
    name    TEXT NOT NULL,
    img_src TEXT NOT NULL
);

INSERT INTO app2 (name, img_src)
VALUES ('UHJhaGE=', 'aharp.jpg');
```

```postgresql
UPDATE app2
SET name = 'QnJubw==', img_src = 'onrb.jpg'
WHERE name = 'UHJhaGE=';
```

## Backup

```shell
# Optional
dc exec pg14 /rds/bin/backup-full.sh
```

## Restore

```shell
rm -r ./postgres_data
```
