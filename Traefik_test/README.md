# Purpose
This folder is used to test traefik load balancer.
1. We are going to build a chat app
2. We want to deploy chat app to Docker Swarm
3. Realize Horizontal scalability (adding more resource instead of upgrading node which is called vertical scalability)

# Requirements
1. Developed on MacOS (Traefik providers do not show correctly on Win10)
2. Install Docker on MacOS
3. Install Node on MacOS (npm is installed with Node)
4. Install Visual Studio Codes (also "Control+Shift+P" to install code to $PATH, so that in shell "code ." will start VS codes)

# file explanations
1. package.json: initially generated by 'npm init -y', and changed with 'npm add fastify'. But the "script" is changed, so that npm start will try to start index.js;
2. index.js: the server scripts;
3. docker-compose.yml: used by 'docker-compose build' and 'docker-compose up'. Here we created 3 docker images, 'traefik' for load balancer, 'service1' running index.js, and 'service2' also running index.js. We want to balance loads on service1 and service2.
4. Dockerfile: used by "build" in 'docker-compose.yml', to build nodejs servers.

# Commands
In Terminal, initiate .git folder and package.json file
```
git init
npm init -y #this will create package.json
code .
```
Later I use Terminal in VS codes
```
npm add fastify #Install fastify which has socket module for chat app
node index.js #to start index.js

docker pull traefik:latest #pull load balancer image.
docker-compose rm -f #rm old images
docker-compose build #build images
docker-compose up #start server, in Win10 use 'docker-compose up -d'
```

# Run codes
1. 'docker-compose rm -f' to clean the images
2. 'docker-compose build' to build images
3. 'docker-compose up' to start all servers
4. Check: localhost:8080 will see traefik dashboard. Refresh '127.0.0.1' to see queries are balanced between load1 and load2.
5. control + c to stop services.
Note: 127.0.0.1 is specified in docker-compose.yml, and in index.js (0.0.0.0) is added so that 127.0.0.1 is binded.
