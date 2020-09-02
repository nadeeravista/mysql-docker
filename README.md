# Overview
This is a simple docker file for you to spin up a MySql server and PhpMyadmin. If you need only need server, you may remove the **phpmyadmin** section from docker-compose.yml file

## Installation steps

##### Prerequests
You must have installed Docker in your system. If you are using a Mac, the Docker Desktop is the ideal tool [Docker Desktop](https://www.docker.com/products/docker-desktop)

##### Set the settings and Install
- You may specify the port you need to run the MySql server. Also you can sepcify the volume location if you nee persistant data each time when you spin up the server
docker-compose.yml
```
    ports:
      - "3306:3306"
    volumes: 
      - ./data/mysql:/var/lib/mysql
      
```
You may set other settings as you wish on the docker-compose.yml

##### Setting Phpmyadmin
```
    environment:
      PMA_HOST: host.docker.internal
      PMA_PORT: 3306
      PMA_ARBITRARY: 1
    restart: always
    ports:
      - 8184:80
```
The mysql port and phpmyadmin PMA_PORT must be same 

- If you have specified a volumes, then share the host computer volume directory using Docker Desktop 
Settings -> Resources -> File Sharing -> Add your host file directory

- Run the following command inside the directory
```
docker-compose build && docker-compose up -d
```

- Your can then access the database server on [localhost:3306](http://localhost:3306)
- you can access database using phpmyadmin using the url [localhost:8184](http://localhost:8184)
            - Server : host.docker.internal
            - User : root
            - Password : root
