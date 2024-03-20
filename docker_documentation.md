Docker Desktop Intro Documentation: Creating Containers using Ubuntu 

 

 

1. Install updates: 

First open your virtual machine and start your ubuntu operating system. 

Once you’ve logged in begin by making sure your system is up to date by entering the commands below. 

 

sudo apt-get update 
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common 
 
 

3. Add the Docker GPG key: 

Once sudo apt update and sudo apt install have processed, start downloading and adding the docker key. 

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - 
 
 

4. Add the Docker repository: 

After that add the repository. 

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" 
 
 

5. Update package lists and install Docker Engine: 

When you are done adding the repository start by installing the docker engine with the commands below. 

sudo apt-get update 
sudo apt-get install docker-ce 
 
 

6. Confirm Docker installation: 

Once you’ve finished installing begin running the docker run hello world command below. 

docker run hello-world 
 
 

This command will download and run a basic "hello world" container, confirming successful installation. 

When I first ran the hello world command I received the following error message below. 

docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.35/containers/create: dial unix /var/run/docker.sock: connect: permission denied. See 'docker run --help'. 

To resolve this, I ran the following commands to run docker as a non-root user to add it to the docker group. 

Create the docker group if it does not exist 

$ sudo groupadd docker 
 

Add your user to the docker group. 

$ sudo usermod -aG docker $USER 
 

Log in to the new docker group 

$ newgrp docker 
 

Check if docker can be run without root 

$ docker run hello-world 
 

Reboot if still got error 

$ reboot 

Once you reboot you should be able to run the hello world command to confirm docker installation. 

Additional notes - reboot may not be required, restarting docker may be sufficient. 

 sudo systemctl restart docker 

7. Pull the CentOS container image: 

To begin pulling the CentOS container image run the command below. 

 

 

docker pull centos:latest 
 
 

8. Run the CentOS container: 

docker run -it centos:latest /bin/bash 
 
 

This command will pull the latest CentOS image and runs it in interactive mode (-it) with a bash shell, which allows you to interact with the container. 

9. Exit the CentOS container: 

To exit the container run the command 

 

exit 
 
 

10. Pull the Kali Linux container image: 

To begin pulling the Kali Linux container image run the command below. 

 

docker pull kalilinux/kali-rolling 
 
 

11. Run the Kali Linux container: 

 

docker run -it kalilinux/kali-rolling /bin/bash 
 
 

This command will pull the latest Kali Linux image and run it in interactive mode (-it) with a bash shell. 

12. Exit the Kali Linux container: 

To exit the container run the command 

 

exit 
