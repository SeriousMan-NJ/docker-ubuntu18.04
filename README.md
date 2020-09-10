# docker-ubuntu18.04

# Basic docker commands
docker build --tag ubuntu18.04-ywshin .
docker run -dit --name ubuntu18.04-ywshin --restart=always -p 20000-20200:20000-20200 -v $PWD/data:/root/dev ubuntu18.04
docker exec -it ubuntu18.04-ywshin /bin/bash
docker rm --force ubuntu18.04-ywshin

# Create user
adduser --gecos '' --uid 1003 ywshin
usermod -aG sudo ywshin
