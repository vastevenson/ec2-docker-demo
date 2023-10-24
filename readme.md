This is a basic flask app docker container. To run it locally, run cmd: `docker-compose up --build` from the project directory in terminal. 

When the container is running, it will be attached to port 80 of the local machine, go to: http://localhost:80 to view the site. 

Flask, by default, is running on port 5000 of the container, but the docker-compose binds host port 80 to container port 5000. 

