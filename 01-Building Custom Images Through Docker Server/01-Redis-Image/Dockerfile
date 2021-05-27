# Use an existing docker image as a base
FROM alpine
# Download and install a dependency
RUN apk add --update redis
# Tell the image what to do when it starts as a container
CMD [ "redis-server" ]
# Then we run the command sudo docker build . (assuming we are in the root dir)
# to build our image

# FROM, RUN, CMD etc are Instructions telling Docker Server what to do

# alpine is a base OS image. In this context, it has a collection of programs
# needed to achieve our goal, that is installing and using redis-server.

# apk add --update redis is a command from alpine OS, and has nothing to do with
# docker

# All arguments to the Instructions