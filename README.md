# docker-ubuntu18.04

## Basic docker commands
```bash
docker build --tag ubuntu18.04-ywshin .
docker run -dit --name ubuntu18.04-ywshin --restart=always -p 20000-20200:20000-20200 -v $PWD/dev:/root/dev ubuntu18.04-ywshin
docker exec -it ubuntu18.04-ywshin zsh
docker rm --force ubuntu18.04-ywshin
```

## Linux server settings
Setup in the docker container.

### Change ssh setting
Open `sshd_config`
```bash
vim /etc/ssh/sshd_config
```
Uncomment and edit following lines
```
Port 20022
ListenAddress 0.0.0.0
ListenAddress ::

PubkeyAuthentication yes

Password Authentication yes
```
Restart sshd server
```bash
service ssh restart
```

### Create your account
Check your `$UID`
```bash
echo $UID # NOTE: execute the command outside of docker container!
```
create account with your `$UID` and `$USER`
For example, I've create `ywshin` account with `1003` UID.
```bash
adduser --gecos '' --uid 1003 ywshin
usermod -aG sudo ywshin
````

### Change default shell script to zsh
ssh into the docker container
```bash
ssh ywshin@docker-container-address
```
```bash
chsh -s /bin/zsh
```
If you logout and login to the container, shell is changed to zsh!
