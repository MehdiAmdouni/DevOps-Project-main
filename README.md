## demo app - developing with Docker

This demo app shows a simple user profile app set up using 
- index.html with pure js and css 
- nodejs backend with express 
- mongodb for data storage

#### To start the application with Docker 

Step 1: Create docker network

    docker network create mongo-network 

Step 2: start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   
    Step 4: open mongo-express from browser

    http://localhost:8081

Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express

Step 6: Start your nodejs application locally - go to `app` directory of project 

    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

#### To start the application with Docker-compose 

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
#### To build a docker image from the application

    docker build -t my-app:1.0 .       
#### Improvments : 
    1- Problem Pulling image from docker hub ( myapp.yaml)
    2- Problem applying ingress files 
    3- Got the idea of Helm charts , still figuring out the way to change the variables to "Values"