# Specify a base image
FROM alpine

# Specify work directory
# Any following command will be executed
# relative to this path in the container
WORKDIR /usr/app

# Install some depenendencies
COPY ./ ./
RUN apk add --update npm
RUN npm install

# Default command
CMD ["npm", "start"]

# sudo docker run -p 8000:8080 petrostrak/nodejs:latest
# Route incoming requests to this port(8000:) on localhost to...
# ...this port(8080) inside the container