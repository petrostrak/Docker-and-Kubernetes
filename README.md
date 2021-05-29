### Docker and Kubernetes
------
Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

#### Docker basic commands
| Command  |      Usage   |
|----------|:-------------:|
| sudo docker ps |  lists all running images |
| sudo docker ps --all |    lists all images that have run   |
| sudo docker create <image> | returns image id |
|sudo docker start -a <image id>|starts container|
|sudo docker system prune|delets all images|
|sudo docker stop <image id>|sends a SIGTERM to process|
|sudo docker kill <image id>|sends a SIGKILL to process|
|sudo docker exec -it <image id>|runs container and attaches stdin - stdout|
|sudo docker exec -it <image id> sh| creates shell in context of given container|
|sudo docker build -t petrostrak/redis:latest .|tags a name to build project|
|sudo docker run -p 5000:8000 <image id>|routes incoming requests on local port (5000) to container port(8000)|
|sudo docker build -f <custom dockerfile name> .|builds image based on custom dockerfile name |
|sudo docker run -p 5000:8000 -v /path-to-placeholder -v $(pwd):/path-to-container <image id>|puts a bookmark(1)|
###### (1) When we use the colon syntax -v $(pwd): we are saying that we want to map up a folder inside the container, to a folder outside the container.
###### When we don't use the colon syntax, -v /path, we essentially saying we want this to be a placeholder for the folder that is inside the container, so don't try to map it up against anything.

#### Dockerfile instructions
------
| Instruction  |      Usage   |
|----------|:-------------:|
| FROM |  specifies a base image |
|RUN|installs dependencies|
|COPY|copies files and folders from local filesystem to the container|
|WORKDIR|any following command will execute relative to the given path in the container|
|CMD|default command|

#### Dockerfile example
```
FROM node:alpine
WORKDIR '/app'
COPY ./package.json /.
RUN npm install
COPY . .
CMD [ "npm", "run", "start" ]
```

#### Docker-compose
------
| Command  |      Usage   |
|----------|:-------------:|
|sudo docker-compose ps|lists all running services based on pwd|
|sudo docker-compose up| runs compose|
|sudo docker-compose up --build|builds/rebuilds compose|
|sudo docker-compose up -d|launches in background|
|sudo docker-compose down|stops containers|

#### Docker-compose instructions
| Instruction  |      Usage   |
|----------|:-------------:|
|version|selects version|
|services|adds desired containers |
|image|specifies the image to use|
|ports|specifies an array of ports to do the mapping|
|restart|specifies a restart policy for a service or server container|
|build|looks at given directory for a Dockerfile and builds image|
##### Overriding dockerfile selection
```
build: 
    context: .  #Look at current working directory
    dockerfile: Dockerfile.dev  #Find the file with that name and use it to build the image
```

##### Restart policies
| Policy  |      Usage   |
|----------|:-------------:|
|no|never attempts to restart|
|always|if it stops for any reason, always attemp to restart|
|on-failure| only restarts if the container stops with an error code|
|unless-stopped|always restarts unless we forcibly stop it|

#### Docker-compose.yml example
```
version: '3'
services: 
    web:
        build: 
            context: .
            dockerfile: Dockerfile.dev
        ports: 
            - "3000":"3000"
        volumes: 
            - /app/node_modules
            - .:/app
```











