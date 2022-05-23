
# Docker
# Step-By-Step Docker Installation on Windows

1. Go to the website https://docs.docker.com/docker-for-windows/install/ and download the docker file. 
***Note: A 64-bit processor and 4GB system RAM are the hardware prerequisites required to successfully run Docker on Windows 10.***

2. Then, double-click on the Docker Desktop Installer.exe to run the installer.
***Note: Suppose the installer (Docker Desktop Installer.exe) is not downloaded; you can get it from Docker Hub and run it whenever required.***

3. Once you start the installation process, always enable Hyper-V Windows Feature on the Configuration page.

4.  Then, follow the installation process to allow the installer and wait till the process is done.

5. After completion of the installation process, click Close and restart. 


# How to Install Docker on Ubuntu: A Step-By-Step Guide

1. Open the terminal on Ubuntu.

2. Remove any Docker files that are running in the system, using the following command:
   $ sudo apt-get remove docker docker-engine docker.io
***After entering the above command, you will need to enter the password of the root and press enter.***

3. Check if the system is up-to-date using the following command:
	$ sudo apt-get update

4.  Install Docker using the following command:
	$ sudo apt install docker.io
***You’ll then get a prompt asking you to choose between y/n - choose y	***

5. Install all the dependency packages using the following command:
	$ sudo snap install docker

6. Before testing Docker, check the version installed using the following command:
	$ docker --version

# How to fix docker: Got permission denied while trying to connect to the Docker daemon socket

7. sudo chmod 666 /var/run/docker.sock
	or 
   sudo chmod 777 /vaar/run/docker.sock

8. Pull an image from the Docker hub using the following command:
   $ sudo docker run hello-world
***Here, hello-world is the docker image present on the Docker hub.***

9.  Check if the docker image has been pulled and is present in your system using the following command:
	$ sudo docker images

10. To display all the containers pulled, use the following command:
	$ sudo docker ps -a

11. To check for containers in a running state, use the following command:
	$ sudo docker ps



