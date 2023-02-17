# docker-to-ecs-project

## Steps

### Run application using docker on EC2 server

1. Create EC2 server on AWS Console (make sure you opened 80 port in security group)
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
6. create private ECR repository on AWS console with any name (like node-react-app)
7. configure your AWS credentials using commands
    * export AWS_ACCESS_KEY_ID=your-access-key
    * export AWS_SECRET_ACCESS_KEY=your-secret-key
    * export AWS_DEFAULT_REGION=your-ecr-region
8. go to ecr repo and copy push commands from ecr and paste in location where docker file exists for login, build, tagging and push image to ecr
9. after running all commands check ecr repo and confirm image exists
10. run docker run command to start the container
    * docker run -d -p 80:80 node-react-app:latest
11. after starting the container copy public ip of EC2 server and paste in browser to see app is working or not