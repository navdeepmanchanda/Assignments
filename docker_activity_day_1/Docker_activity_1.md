                            Docker Activity Day-1

Run a ubuntu 16.04 container
  - Name the container: "ub01"
  - Set the hostname of container: "ub.example.com"
  - Assign memory : 800 MB
  - Set environment variables
      - NAME: $(yourname)
      - ORG: Opstree
      - TEAM: Ninja
      - TASK: Docker
  - Set above defined variables from a file
- Set container default login directory to /var/log
![](https://github.com/navdeepmanchanda/Assignments/blob/master/docker_activity_day_1/Media/Docker_activity_day1_Ass_1_pic1.png)
![](https://github.com/navdeepmanchanda/Assignments/blob/master/docker_activity_day_1/Media/docker_day1_activity1_ass_1_pic2.png)

				Docker Lifecycle

- Start an Ubuntu 14.04 container
- Get /var/log/dpkg.log on your host machine from container
- Delete /var/log/dpkg.log that file from container
- Create a new image of the current state of container and it "ubuntu:custom"
- Remove the container
- Run a new container of fresh image "ubuntu:custom"
- Check for the earlier deleted file inside the container
- Copy that file to container from host machine
- Recheck the file inside container.

Solution:
docker cp navdeep:/var/log/dpkg.log /home/guggu  ->copy from container to host machine
docker exec -it navdeep  -> to enter into container
rm -f var/log/dpkg.log  ->to remove file in container
ctrl +p+q  ->back to host machine 
docker commit -a "Navdeep Manchanda" -m "Commit without dpkg.log file" navdeep log:nav1 ->create image of running container at current state
docker rm -f 29901a7554c0  -> to remove container
docker run -it log:nav1 bash  -> creation of new container using image
docker exec -it 0cfc6d355991 bash   ->enter into new container
Checked for dpkg.log file but not found.
docker cp  dpkg.log 0cfc6d355991:/var/log ->manually copy dpkg.log file to container
                                  
                                  Docker Inspection

- Run a ubuntu container and inspect the following info
  - IP Address
  - Mac Address
  - Hostname
  - Container Name
- Environment Variables
Solution: 
docker inspect -f='{{.Config.Env}}{{.Name}}{{.Config.Hostname}}{{range .NetworkSettings.Networks}}{{.IPAddress}}{{.MacAddress}}{{end}}' 0cfc6d355991
Output:
[NAME=navdeep ORG=Opstree TEAM=ninja TASK=docker PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin]/suspicious_edison0cfc6d355991172.17.0.302:42:ac:11:00:03
![](https://github.com/navdeepmanchanda/Assignments/blob/master/docker_activity_day_1/Media/Docker_day1_ass_1_Pic1.png)
                                     
                                     Docker Monitoring:
 Run 2 containers 
  - Check the following resource utilization
      - Memory
      - CPU
      - Disk I/O
      - Net I/O
  - List down the process running inside the containers                                     
![](https://github.com/navdeepmanchanda/Assignments/blob/master/docker_activity_day_1/Media/Docker_Monitoring.png)
Solution:
docker stats --all --format "table {{.Container}}\t{{.CPUPerc}}\t{{.MemUsage}}\t{{.BlockIO}}\t{{.NetIO}}" suspicious_edison tender_elbakyan
