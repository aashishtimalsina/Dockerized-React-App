# Dockerized React App

This repository contains a simple guide to create and Dockerize a React app for development. Follow the steps below to get started.

## Prerequisites

Before you begin, make sure you have the following prerequisites installed on your system:

- [Docker](https://docs.docker.com/get-docker/)
- Node.js and npm

## Step 1: Create a New React App

To create a new React app, follow these commands:

```
npx create-react-app docker-react
cd docker-react 
```

## Step 2: Create a .dockerignore File

```
node_modules
build
.dockerignore
Dockerfile
Dockerfile.prod
```

## Step 3: Create a Dockerfile
```
FROM node:13.12.0-alpine

WORKDIR /app

ENV PATH /app/node_modules/.bin:$PATH

COPY package.json ./
COPY package-lock.json ./
RUN npm install --silent
RUN npm install react-scripts@5.0.1 -g --silent

COPY . ./

CMD ["npm", "start"]
```

## Step 4: Build a Docker Image
```
docker build -t dockerreactimage:dev .
```

## Step 5: Create a Docker Container
```
docker run -it -p 3000:3000 dockerreactimage:dev
```

### Your React app should now be running in a Docker container and accessible at http://localhost:3000.
