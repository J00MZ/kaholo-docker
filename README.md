# Production Map - Docker Config

This is a dockerized implementation of production-map (http://www.productionmap.com/)
Current implementation includes mongodb, production-map-server and production-map-base-agent.

To build the images first enter the relevant folder for example pm-server
```
cd pm-server
```
then build the docker image
```
docker build -t pm/server .
```

To run the server image use the following docker command:
```
docker run -d -p 8080:8080 --name="pmServer" pm/server
```

Next build the base agent
```
cd pm-base-agent
docker build -t pm/base-agent .
```

Now run the agent while using link inorder to bind it to the server
```
docker run -d --link pmServer pm/base-agent
```

edit the file with the relevant fields (server address, agent address, agent port)

If you want to make sure your mongodb data persists to your local machine you can do this:

```
docker volume create --name production-map-mongo
docker run -d -p 8080:8080 --name=pmServer -v production-map-mongo:/var/lib/mongodb pm/server
```

All processes on the image are managed via supervisord and stdout is merged into the main container process.

Special Thanks for ericuldall who created the initial dockerfiles.
