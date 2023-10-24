This is a basic flask app docker container. To run it locally, run cmd: `docker-compose up --build` from the project directory in terminal. 

When the container is running, it will be attached to port 80 of the local machine, go to: http://localhost:80 to view the site. 

Flask, by default, is running on port 5000 of the container, but the docker-compose binds host port 80 to container port 5000. 

The following steps below only work if your local machine has same cpu arch as the ec2 instance (x86 or arm):
To build the docker image locally, run command: `docker build -t ec2-flask-demo:v1.0 .` from project dir

Next, we need to save the image as a tarball to compress the artifact before uploading it to the ec2 instance, run cmd: `docker save -o ec2-flask-demo.tar ec2-flask-demo:v1.0` - there should now be a .tar file in the project dir. 

Now, we are going to upload the tar file to the ec2 instance using scp: `scp -i vs-kp-1.pem ec2-flask-demo.tar ec2-user@3.142.211.164:/home/ec2-user/docker_images`
We get an error if we haven't set the permissions on the .pem file, need to run: `chmod 600 vs-kp-1.pem`

The size of the demo docker image tar file is 162 MB - if you run `ls` from within the ec2 instance, we can now see it. 



