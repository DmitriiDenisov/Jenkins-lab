# Jenkins-lab

### How to install

Instructions: https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-18-04-ru

If fails after running `sudo apt install jenkins` with an error saying that could not find Java =>

`sudo apt install openjdk-9-jre`
`sudo apt install openjdk-8-jre`
Open `sudo vi /etc/init.d/jenkins`
Finally, append path to the new java executable (line 16): `PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/lib/jvm/java-8-openjdk-amd64/bin/`

Source: https://stackoverflow.com/questions/39621263/jenkins-fails-when-running-service-start-jenkins

If still fails saying that port is already in use then: 
1. `sudo vim /etc/default/jenkins`
2. Change `HTTP_PORT`
3. `sudo systemctl start jenkins`

