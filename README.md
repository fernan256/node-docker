# Build image
docker build -t <image-name> <directory>
docker build -t <image-name> .

# Run container
docker run -p <port>:<port> -d --name <container-name> <iamge-name>

docker run -v ~/Documentos/nodeCourses/node-docker:/app -p 3000:3000 -d --name node-app node-docker-v1

docker run -v $(pwd):/app -p 3000:3000 -d --name node-app node-docker-v1

docker run -v $(pwd):/app -v /app/node_modules -p 3000:3000 -d --name node-app node-docker-v1

docker run -v $(pwd):/app:ro -v /app/node_modules -p 3000:3000 -d --name node-app node-docker-v1

docker run -v $(pwd):/app:ro -v /app/node_modules -e PORT=4000 -p 3000:4000 -d --name node-app node-docker-v1

docker run -v $(pwd):/app:ro -v /app/node_modules --env-file ./.env PORT=4000 -p 3000:4000 -d --name node-app node-docker-v1

# Delete contianer
docker rm node-app -f
docker rm node-app -fv (Delete volumen associated to the container)

# Access to container
docker exec -it <container-name> bash

# List container
docker ps

docker ps -a

# Show container logs
docker logs <container-name>

# Docker compose
docker-compose up --build
docker-compose up
docker-compose up -d
docker-compose down -v

# Docker compose with multiple environment yaml per env
docker-compose -f docker-compose.yaml -f docker-compose.dev.yaml up -d
docker-compose -f docker-compose.yaml -f docker-compose.prod.yaml up -d --build (flag to rebuild)
