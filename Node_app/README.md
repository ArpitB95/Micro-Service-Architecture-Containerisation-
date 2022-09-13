### Building a Docker image for our node app
- create a micro-service for node-app 
- create Dockerfile inside the app folder
- create a script to package our node app in an image
- create a container of our image
- should load it on port 3000 or port 80
- push it to docker hub


## steps to create Docker image for node app
- Create a new folder and paste app folder inside that
- Create Dockerfile inside the app folder



- Dockerfile:
```
# base image
FROM node

# label
LABEL MAINTAINER=ARPIT

# inside the container what would be the default wrk dir

# pwd home/vagrat/ubuntu

#wrkdir /usr/src/app
WORKDIR /usr/src/app


# copy dependencies and app folder
COPY package*.jason ./
COPY . .
# copy all files with .json extension to default location

# run some commands such as npm install
RUN apt update
RUN npm install -g npm@7.20.6
RUN npm install express
RUN npm install mongoose



# expose the port 3000
EXPOSE 3000

CMD ["node", "app.js"]

# BUILD THIS IMAGE - PACKAGE IT UP 

```

- Now, build docker image from dockerfile by running
- 'docker build -t dockerhub_name/name_of_image (give any name you want)

- 'docker build -t arpitb95/eng122_node_app .'
  
- Now image will be created, you can check this by 'docker images'
  
- Now, create a container from that image
- 'docker run -d -p 3000:3000 image_name'
- 'docker run -d -p 3000:3000 eng122_node_app'

- You can check container is running or not by 'docker ps'
  
