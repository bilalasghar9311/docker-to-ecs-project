# docker-to-ecs-project

## Steps

### Run application using docker on EC2 server

Create EC2 server on AWS Console
ssh into server
install git using command
* sudo yum install git
clone the code
install the docker on server using commands
* sudo yum update
* sudo yum install docker -y
* sudo systemctl start docker
* sudo usermod -aG docker ec2-user
* exit (exit from server and ssh again)
go to the location where Dockerfile exists and run the docker build command to create the image