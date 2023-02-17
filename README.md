# docker-to-ecs-project

## Steps

### Run application using docker on EC2 server

1. Create EC2 server on AWS Console
2. ssh into server
3. install git using command
    * sudo yum install git
4. clone the code
5. install the docker on server using commands
    * sudo yum update
    * sudo yum install docker -y
    * sudo systemctl start docker
    * sudo usermod -aG docker ec2-user
    * exit (exit from server and ssh again)
6. go to the location where Dockerfile exists and run the docker build command to create the image