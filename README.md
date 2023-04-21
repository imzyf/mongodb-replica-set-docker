# MongoDB Replica Set

Without further due let’s get started.

```bash
mkdir -p runtime/data_db{1,2,3} && \
mkdir -p runtime/data_configdb{1,2,3}
```

```
hostname -f
```

## bootstrap

```bash
DELAY=10

docker-compose --file docker-compose-replicaset.yml down
docker rm -f $(docker ps -a -q)
docker volume rm $(docker volume ls -q)

docker-compose --file docker-compose-replicaset.yml up -d

echo "****** Waiting for ${DELAY} seconds for containers to go up ******"
sleep $DELAY

docker exec mongo1 /scripts/rs-init.sh
```

## References

- [](https://blog.devgenius.io/how-to-deploy-a-mongodb-replicaset-using-docker-compose-a538100db471)
