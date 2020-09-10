# docker-ubuntu18.04

## Basic docker commands
```bash
docker build --tag ubuntu18.04-ywshin .
docker run -dit --name ubuntu18.04-ywshin --restart=always -p 20000-20200:20000-20200 -v $PWD/data:/root/dev ubuntu18.04
docker exec -it ubuntu18.04-ywshin zsh
docker rm --force ubuntu18.04-ywshin
```

## Create user
```bash
adduser --gecos '' --uid 1003 ywshin
usermod -aG sudo ywshin
````
