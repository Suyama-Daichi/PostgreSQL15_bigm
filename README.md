# postgres15_bigm

## What's this ?
[pg_bigm v1.2](https://pgbigm.osdn.jp/) をインストールしたDocker Imageです。

[symdit/postgresql15-bigm - Docker Hub](https://hub.docker.com/repository/docker/symdit/postgresql15-bigm)

## How to use
```bash
docker pull symdit/postgresql15-bigm
```

create `docker-compose.yml` file like this
```yml
version: '3.9'

services:
  db:
    image: symdit/postgresql15-bigm
    restart: always
    container_name: postgresql15-bigm
    ports:
      - '5433:5432'
    volumes:
      - ./script:/docker-entrypoint-initdb.d
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: tests
      PGDATA: /var/lib/postgresql/data/pgdata

```

```
docker-compose up -d
```

## コンテナ立ち上げ後にSQLを実行する
`script`配下にsqlファイルを置くと、コンテナ立ち上げ後に任意のSQLを実行することができます。
