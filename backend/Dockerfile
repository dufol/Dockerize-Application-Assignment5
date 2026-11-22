
## Dockerfile for the frontend application

FROM node:14-alpine

## Set the working directory inside the container
WORKDIR /app

## Copy package.json and package-lock.json to the working directory
COPY package*.json ./

## Install dependencies
RUN npm install

## Copy the rest of the application code to the working directory
COPY . .

## Create a directory for the public files
RUN mkdir -p /app/public

## Expose the port that the application will run on
EXPOSE 8080

## Start the application
CMD ["npm", "start"]