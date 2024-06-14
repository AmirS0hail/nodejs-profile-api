## with these commands create and start two docker containers

# commands
## create network where the containers talk to each other using just the container name and no host, port necessery

## create docker network
docker network create mongo-network

## ran two docker run command with options and environment variables

## start mongodb
docker run -d \
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
-net mongo-network \
--name mongodb \
mongo

## start mongo-express 
docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--net mongo-network \
--name mongo-express \
mongo-express