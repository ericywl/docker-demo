# Docker Demo

## With Docker

### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: Start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: Start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

## With Docker Compose

### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: Open mongo-express from browser

    http://localhost:8081

Step 3: Create `eric-db` _db_ and `eric-collection` _collection_ and _document_ with `{some_id: 1, data: "some dynamic data loaded from db"}` in mongo-express
    

Step 4: Access you nodejs application UI from browser

    http://localhost:3000