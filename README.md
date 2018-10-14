# Kaholo - Docker Config

This is a dockerized implementation of Kaholo (https://kaholo.io/)
Current implementation includes mongodb, kaholo-server and kaholo-agent.

## Running kaholo server Using Docker compose
You can run the pm-server image using docker compose
Navigate to the pm-server directory and run docker compose
```
cd pm-server
docker-compose up -d
```
wait until the build process is done and then navigate to the server url using the 8080 as the port.

## Connecting base agents

Navigate to the base-agent directory and build the image.
you can edit the baseagent.js file with the relevant fields before altough the image comes with default params for conneting to the server (server address, agent address, agent port).
```
cd pm-base-agent
docker build -t pm/base-agent .
```

Now run the agent while using link inorder to bind it to the server
```
docker run -itd --network=pmserver_default pm/base-agent
```

## Build the server image alone
To build the images first enter the relevant folder for example pm-server
```
cd pm-server
```
then build the docker image
```
docker build -t pm/server .
```

Special Thanks for ericuldall who created the initial dockerfiles.
