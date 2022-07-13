## Create Bridge
```sh
docker network create notes-api-network
```

## Create Named Volume for DB persistence

```sh
docker volume create notes-db-data
```

## Run Database Server as container
```sh
docker container run \
    --detach \
    --volume notes-db-data:/var/lib/postgresql/data \
    --name=notes-db \
    --env POSTGRES_DB=notesdb \
    --env POSTGRES_PASSWORD=secret \
    --network=notes-api-network \
    postgres:12
```
