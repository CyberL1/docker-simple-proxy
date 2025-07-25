# What is this?

This is an automatic proxy for docker containers.
It gives you access to a docker container without needing to publish its ports to the host.

# How to use this?

1. Create a network for the proxy:
  ```bash
  docker network create simple-proxy
  ```

2. Run the proxy using:
   ```bash
   docker run -d -p 80:80 --name docker-simple-proxy -e PROXY_DOMAIN=localhost --network simple-proxy ghcr.io/cyberl1/docker-simple-proxy
   ```

3. Run another container connected to the proxy network:
  ```bash
  docker run -d --name another-container --network simple-proxy nginx:alpine
  ```

4. Go to http://another-container.localhost in your browser and see the result. If your container is listening on diffrent port (i.e 8080), then go to http://another-container-8080.localhost
