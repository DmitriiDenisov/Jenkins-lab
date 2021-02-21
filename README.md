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

### Some examples

You can find examples of jobs in folder `examples` in this repo. All of them were built based on [Tutorials](https://www.youtube.com/watch?v=cyb10iplv7U&list=PLg5SS_4L6LYvQbMrSuOjTL1HOiDhUE_5a&ab_channel=ADV-IT)

In order to import them into Jenkins (details find below in Jenkins CLI section): 
`java -jar jenkins-cli.jar -auth USERNAME:USERPASS -s http://localhost:9090 create-job newmyjob < myjob.xml`


### Useful Commands:
```
systemctl enable jenkins # Enable the Jenkins service to start automatically.
service jenkins start
service jenkins status
service jenkins restart
```

### Install Plugins:

If you can't find necessary plugin in Web UI then:

1) Go to http://updates.jenkins.io/download/plugins and find page of your plugin

2) After you know the name of necassary plugin (for example, it is "credentials") go by link: http://updates.jenkins.io/download/plugins/credentials/

3) Download *.hpi file

4) In Web UI in "Manage Plugins" go to Advanced and there upload this *.hpi file

### Reset Password: 

Instructions: https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-reset-jenkins-admin-users-password/

### Touble shooting

Error "Docker: Got permission denied while trying to connect..." then  `sudo usermod -a -G docker jenkins`

### Jenkins CLI

1. Download jar: `wget http://34.121.35.34:9090/jnlpJars/jenkins-cli.jar`

2. Check that all is correct: `java -jar jenkins-cli.jar -auth USERNAME:USERPASS -s http://localhost:9090 who-am-i`

3. Export Job: `java -jar jenkins-cli.jar -auth USERNAME:USERPASS -s http://localhost:9090 get-job myjob > myjob.xml`

4. Import Job: `java -jar jenkins-cli.jar -auth USERNAME:USERPASS -s http://localhost:9090 create-job newmyjob < myjob.xml`

### Tutorials [Russian]

[Tutorials](https://www.youtube.com/watch?v=cyb10iplv7U&list=PLg5SS_4L6LYvQbMrSuOjTL1HOiDhUE_5a&ab_channel=ADV-IT)

Watch videos 

№1: Intro

№3: Web UI and settings 

№5: Important tutorial. Shows how to build most simple jobs (with build, test and deployment stages) + how to do ssh deployment

№6: (optional) how to connect few servers . only need in case you have large amout of jobs

№7: (optional) Jenkins CLI (how to import/export jobs)

№8: Deployment from GitHub (your username should match with user in ssh-key, for this use `ssh-keygen -C DmitriiDenisov -f new_key`)

№9: (optional) Jenkins Build Triggers

№ 10: Jenkins trigger from GitHub, Jenkins webhook

№11: Build with parameters
