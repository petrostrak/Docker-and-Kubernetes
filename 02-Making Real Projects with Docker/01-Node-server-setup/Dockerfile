# Specify a base image
FROM alpine

# Install some depenendencies
COPY ./ ./
RUN apk add --update npm
RUN npm install

# Default command
CMD ["npm", "start"]