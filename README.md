# Jenkins-lab

### How to install

Instructions: https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-18-04-ru

If fails after running `sudo apt install jenkins` with an error saying that could not find Java =>

1. `sudo apt install openjdk-9-jre`
2. `sudo apt install openjdk-8-jre`
3. Open `sudo vi /etc/init.d/jenkins`
4. Finally, append path to the new java executable (line 16): `PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/lib/jvm/java-8-openjdk-amd64/bin/`

[Source](https://stackoverflow.com/questions/39621263/jenkins-fails-when-running-service-start-jenkins)

If still fails saying that port is already in use then: 
1. `sudo vim /etc/default/jenkins`
2. Change `HTTP_PORT`
3. `sudo systemctl start jenkins`

### Reset Password: 

Instructions: https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-reset-jenkins-admin-users-password/

### Tutorials [Russian]

https://www.youtube.com/watch?v=cyb10iplv7U&list=PLg5SS_4L6LYvQbMrSuOjTL1HOiDhUE_5a&ab_channel=ADV-IT
