# Use an existing docker image as a base
FROM alpine
# Download and install a dependency
RUN apk add --update redis
# Tell the image what to do when it starts as a container
CMD [ "redis-server" ]
# Then we run the command sudo docker build . (assuming we are in the root dir)
# to build our image