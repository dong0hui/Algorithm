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

docker-compose rm -f #rm old images
docker-compose build #build images
docker-compose up #start server
```
