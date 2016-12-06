# Build an image from a Dockerfile
docker build -t websphere-liberty:was6profile .

# Run a image in a new container
docker run -d -p 9080:9080 -p 9443:9443 -t websphere-liberty:was6profile

# List containers
docker ps

# Stop one or more running containers
docker stop <CONTAINER_ID>
