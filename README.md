# Production Map - Docker Config

This is a dockerized implementation of production-map (http://www.productionmap.com/)
Current implementation includes mongodb, production-map-server and production-map-base-agent.

You can build an image yourself or pull a copy from my dockerhub repo (https://hub.docker.com/r/thelettere/production-map/)

To run the image use the following docker command:
```
docker run -d -p 8080:8080 theletter/production-map:latest
```

All processes on the image are managed via supervisord and stdout is merged into the main container process.
