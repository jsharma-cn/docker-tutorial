# Docker Installation
brew install colima
# Colima start
colima start --cpu 2 --memory 4
colima start --cpu 1 --memory 2 --disk 10
# Colima stop
colima stop

# Docker basic commands
1. List docker process.
Docker ps
2. List a network & Create
docker network ls
docker network create my-network
3. Mongo Docker run
docker run -d --network my-network --name my-mongo \
	-e MONGO_INITDB_ROOT_USERNAME=admin \
	-e MONGO_INITDB_ROOT_PASSWORD=admin \
	mongo

docker logs 9faccfe8a859
docker stop 9faccfe8a859
docker start 9faccfe8a859
# Go to continer inside
docker exec -it 9faccfe8a859 /bin/bash
# Remove docker container
docker ps -a
docker rm 9faccfe8a859
# Remove docker image
docker rmi mongo
# Docker start with port binding
docker run -d --network my-network --name my-mongo \
	-e MONGO_INITDB_ROOT_USERNAME=admin \
	-e MONGO_INITDB_ROOT_PASSWORD=admin \
    -p 27017:27017 \
	mongo

# Mongo Express
docker images
docker run -d --network my-network --name mongo-express \
 -e ME_CONFIG_MONGODB_SERVER=my-mongo \
 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
 -e ME_CONFIG_MONGODB_ADMINPASSWORD=admin \
 -p 8081:8081 \
 mongo-express
