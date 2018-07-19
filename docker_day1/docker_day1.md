           Docker assignment Day 1
       Assignment 1:
    1. Use official shell script to install and configure Docker on your control machine.
Solution:
	 $ curl -fsSL get.docker.com -o get-docker.sh
	  $ sh get-docker.sh
	----------------------------------------------------------
2.	Start Docker service and check status of the same.
		Soluation:
			root@guggu-ThinkPad-T410:/# systemctl start docker
			root@guggu-ThinkPad-T410:/# systemctl status docker
		Output:
			● docker.service - Docker Application Container Engine
   			Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor 	preset: enabled)
   			Active: active (running) since Sun 2018-07-15 13:18:53 IST; 2 days ago
     			Docs: https://docs.docker.com
 			Main PID: 32079 (dockerd)
    			Tasks: 35
   			CGroup: /system.slice/docker.service
           		├─32079 /usr/bin/dockerd -H fd://
           		└─32101 docker-containerd --config /var/run/docker/containerd/containerd.toml
------------------------------------------------------------------------------
	3.Enable Docker service to start at every machine reboot.

Solution:
root@guggu-ThinkPad-T410:/# systemctl enable docker
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker
--------------------------------------------------------------------
       4. Display Docker version.
		root@guggu-ThinkPad-T410:/# docker -v
		Docker version 18.05.0-ce, build f150324
     --------------------------------------------------------------------
	5.Configure non root user to run docker commands without sudo
		Solution:
			useradd docekr_user
			groupadd docker
			usermod -aG docker docker_user
	-----------------------------------------------------------------------------------
	6.Type docker on commandline and read output i.e containing related commands.
There are various commands which can be associated to docker and perform different functions.
	----------------------------------------------------------------------
	7. Display System information using Docker.
	Solution:
		root@guggu-ThinkPad-T410:$ docker system info

	-------------------------------------------------------------------------------------
	8.Check whether you can access/download images from DockerHub or not
  ![](https://github.com/navdeepmanchanda/Assignments/blob/master/docker_day1/media/docker_assign_1.png)
