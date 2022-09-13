# Micro-Service-Architecture-Containerisation-


### What is Micro service architecture?
- A microservices architecture is a type of application architecture where the application is developed as a collection of services. It provides the framework to develop, deploy, and maintain microservices architecture diagrams and services independently.

![image](https://user-images.githubusercontent.com/110182832/189628948-def60139-577c-4c94-99bf-acf6b25f305f.png)

### What is containerisation ?
- Containerization is a form of virtualization where applications run in isolated user spaces, called containers, while using the same shared operating system (OS). 
- One of the benefits of containerization is that a container is essentially a fully packaged and portable computing environment.

### What is Docker ?
- Docker is a software platform that simplifies the process of building, running, managing and distributing applications.
- It does this by virtualizing the operating system of the computer on which it is installed and running.


### Why companies uses Docker ?
- The top reason enterprises are using Docker is to help them deploy across multiple systems, migrate applications, and remove manual reconfiguration work.
- Because application dependencies are built into containers, Docker containers significantly reduce interoperability concerns


### Benefits of Containerisation and Docker:
- Caching a cluster of containers.
- Flexible resource sharing.
- Scalability - many containers can be placed in a single host.
- Running your service on hardware that is much cheaper than standard servers.

### When to use Docker:
- Microservices-based apps
- Pre-deployment application testing
- Early application development
- Multi-cloud or hybrid cloud applications

### When not to use Docker:
- Security considerations.
- GUI applications
- Small-scale deployments



## Virtualisation V/S Containerisation:
- Virtualization enables you to run multiple operating systems on the hardware of a single physical server, 
   while containerization enables you to deploy multiple applications using the same operating system on a single virtual machine or server.
   
   
   
   ![image](https://user-images.githubusercontent.com/110182832/189630397-f4e6151b-fc83-4b72-97cc-8653de9aabea.png)
   
   
   ## Setting up Docker:
   - Download Docker for windows: https://docs.docker.com/desktop/install/windows-install/
   - Install Docker by running the setup file
   - After installing Docker, a new window will pop-up with wsl installation steps
   - click on the link on that window and follow the steps
   
   
   <img width="562" alt="image" src="https://user-images.githubusercontent.com/110182832/189693587-83d8494b-5079-448c-a550-ea1af83ba251.png">
   
   - To check if Docker is installed successfully on local host, open the Docker Desktop and at the bottom left the symbol of docker will turn greenish blue or if 
    you take your cursor to the image, it will say 'Engine is running'.
    
    
    
    ### You can run Docker commands from anywhere in the terminal
    
    - Open GitBash terminal and run docker commands
    - 'docker images' - will show the docker images
    - 'docker ps' - will show the containers
    
    <img width="493" alt="image" src="https://user-images.githubusercontent.com/110182832/189698037-66440390-858b-4f38-b5f1-7d6ef590089c.png">


    - 'docker ps -a' - will show all the containers
    
    - 'docker run -p 80:80 nginx'  # will run nginx image (If it's not available on localhost then it'll download from docker)
    - 'docker run -d -p 80:80 nginx' ## will run nginx image on port 80 and detached
    
    ### To stop the container
    'docker stop container ID'  # Ex:  docker stop 52234a5cc79b  (To find the container id run 'docker ps')
    
    <img width="501" alt="image" src="https://user-images.githubusercontent.com/110182832/189698226-bab76829-304d-4cb8-b7fc-654e6dea0a56.png">
    
    - If above command doesn't work then forcefully stop it by
    - 'docker stop container ID -f'
    
    ### To start 
    'docker start container ID'
    
    ### To delete container
    - 'docker rm cont Id -f'
    
    
    ### To enter the container
    
    'docker exec -it cont ID bash'  ## (EX: 'docker exec -it 52234a5cc79b bash' )

### Inside the container
- To check the system run 'uname' or 'uname-a'

### Go to root html file of nginx
- cd /usr/share/nginx/html
- From that location 
- run 'apt-get update'
- 'apt install sudo'
- 'apt install nano'

- if you want to change the file then 'sudo nano index.html'


## How to push from localhost to Dockerhub:
- Name your local images using one of these methods:
- Link for reference: https://docs.docker.com/docker-hub/repos/

### Replace everything isndie '' with your details or see above link or below image
- When you build them, using docker build -t 'hub-user'/'repo-name'[:'tag']
- By re-tagging an existing local image docker tag 'existing-image id' 'hub-user'/'repo-name'[:tag]
- By using docker commit 'existing-container id' 'hub-user'/'repo-name'[:'tag'] to commit changes
- Now you can push this repository to the registry designated by its name or tag.

 - docker push hub-user/repo-name:tag

<img width="502" alt="image" src="https://user-images.githubusercontent.com/110182832/189703310-4cd9a011-2437-4f5d-88cd-a17e23910ddc.png">



 ### If you get permission access denied error then run following commands:
 
 - 'docker login -u "myusername" -p "mypassword" docker.io'  ## add your username and password of your dockerhub
 - then 'docker push <hub-user>/<repo-name>:<tag>'   ## Here hub-user is username of dockerhub and repo-name is name of repo you want to push to
 
 <img width="441" alt="image" src="https://user-images.githubusercontent.com/110182832/189702356-bb033281-c9ef-43a2-9a65-cd373f663a6a.png">




<img width="502" alt="image" src="https://user-images.githubusercontent.com/110182832/189702661-267b5e3b-0d2c-4c9d-b886-2d3c341e6365.png">



   
 ## Host Static Website in Docker Container:
   
- move file from localhost to container
- delete existing file
- send file.html from localhost to container
- copy data from a to b
- docker cp command : cp source-address destination-address

### How to move file from localhost to container:
- docker cp /home/(name)/(folder_name)/(file_name)  (container_id):/(to_the_place_you_want_the_file_to_be)
   
- 'docker cp /c/Users/bhadr/eng122_docker/index.html 21174c201611:/usr/share/nginx/html'

