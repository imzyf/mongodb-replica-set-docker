# MongoDB Replica Set

Without further due let’s get started.

```
hostname -f
```

## bootstrap

```bash
DELAY=10

docker compose --file docker-compose-replicaset.yml down
docker rm -f $(docker ps -a -q)
docker volume rm $(docker volume ls -q)

docker compose --file docker-compose-replicaset.yml up -d

echo "****** Waiting for ${DELAY} seconds for containers to go up ******"
sleep $DELAY

docker exec mongo1 /scripts/rs-init.sh
```

```bash
docker compose exec mongo1 mongo
```

## References

- [mongo | hub.docker](https://hub.docker.com/_/mongo)
- [mongo-express | hub.docker](https://hub.docker.com/_/mongo-express)
- [How to deploy a MongoDB replica set using docker-compose](https://blog.devgenius.io/how-to-deploy-a-mongodb-replicaset-using-docker-compose-a538100db471)
