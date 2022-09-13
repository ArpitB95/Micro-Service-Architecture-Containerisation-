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