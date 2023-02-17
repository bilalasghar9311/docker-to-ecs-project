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

### Run application using ECS

1. create new vpc for ecs on AWS console
2. create 6 subnets (3 public and 3 private)
3. create security group for load balancer with open 80 port
4. create security group for ecs cluster with inbound to load balancer security group
5. create a target group of instance type
6. create a application load balancer using 3 public subnets, select a security group you create earlier for load balancer and then select target group you created earlier
7. create ssh key pair for ecs servers
8. create ECS cluster with EC2 option
    * select Amazon Linux 2 in OS
    * select t2.micro instance type
    * select key pair you created earlier
    * select 3 private subnets
    * select capacity minimum 1 and maximum 2
9. create task definition, in container 1
    * copy the ecr image url and tag and paste in image URI
    * container port 80
    * select EC2 type
10. create service inside cluster
    * select launch type EC2
    * select application type Service
    * select task definition you created earlier
    * in load balancer select application
    * select load balancer you created earlier
    * select target group you created earlier