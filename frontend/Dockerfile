#Build stage
FROM node:18-alpine as build-stage

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .    

## Create a directory for the public files
ARG VITE_API_URL=http://localhost:5000

## Set the environment variable for the API URL
ENV VITE_API_URL=$VITE_API_URL


# Build the application
RUN npm run build

Production stage
FROM nginx:alpine 

# Copy the built application from the build stage to the Nginx container
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Expose the port that Nginx will run on
EXPOSE 80   

# Start Nginx when the container starts
CMD ["nginx", "-g", "daemon off;"]