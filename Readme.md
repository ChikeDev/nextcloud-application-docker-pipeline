The apache image contains a webserver and exposes port 80. To start the container type:
docker run -d --name   sociaapp   -p 8080:80 757750585556.dkr.ecr.ca-central-1.amazonaws.com/nextcloudapp:4

Testing push to ecr

RUNNING THE APPLICATION USING THE ERC BUILT IMAGE. 

docker run -d --name   sociaapp   -p 8080:80  722351645273.dkr.ecr.us-east-1.amazonaws.com/nextcloudapp:2