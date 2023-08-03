# Tomcat installation on EC2 instance
1. EC2 instance with Java 11
### Install Apache Tomcat
1. Download tomcat packages from  https://tomcat.apache.org/download-10.cgi onto /opt on EC2 instance
   # Create tomcat directory
   cd /opt
   wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.11/bin/apache-tomcat-10.1.11.tar.gz
   tar -xvzf /opt/apache-tomcat-10.1.11.tar.gz
   ```
2. given executing permissions to startup.sh and shutdown.sh which are under bin. 
   ```sh
   chmod +x /opt/apache-tomcat-<version>/bin/startup.sh 
   chmod +x /opt/apache-tomcat-<version>/bin/shutdown.sh
   ````
3. create link files for tomcat startup.sh and shutdown.sh 
   ```sh
   ln -s /opt/apache-tomcat-<version>/bin/startup.sh /usr/local/bin/tomcatup
   ln -s /opt/apache-tomcat-<version>/bin/shutdown.sh /usr/local/bin/tomcatdown
   tomcatup
   ```
#### Check point :
access tomcat application from browser on port 8080  
 - http://<Public_IP>:8080

  Tomcat and Jenkins runs on ports number 8080. Hence changed tomcat port number to 8090. Changed port number in conf/server.xml file under tomcat home
   ```sh
 cd /opt/apache-tomcat-<version>/conf
# updated port number in the "connecter port" field in server.xml
# restarted tomcat after configuration update
tomcatdown
tomcatup
```
#### Check point :
Accessd tomcat application from browser on port 8090  
 - http://<Public_IP>:8090

1. now application is accessible on port 8090. but tomcat application doesn't allow to login from browser. changing a default parameter in context.xml does address this issue
   ```sh
   #search for context.xml
   find / -name context.xml
   ```
2. above command gives 3 context.xml files. comment (<!-- & -->) `Value ClassName` field on files which are under webapp directory. 
After that restart tomcat services to effect these changes. 
Below 2 files are updated. 
   ```sh 
   /opt/tomcat/webapps/host-manager/META-INF/context.xml
   /opt/tomcat/webapps/manager/META-INF/context.xml
   
   # Restart tomcat services
   tomcatdown  
   tomcatup
   ```
3. Updated users information in the tomcat-users.xml file
In tomcat home directory , Added below users to conf/tomcat-users.xml file
   ```sh
	<role rolename="manager-gui"/>
	<role rolename="manager-script"/>
	<role rolename="manager-jmx"/>
	<role rolename="manager-status"/>
	<user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
	<user username="deployer" password="deployer" roles="manager-script"/>
	<user username="tomcat" password="s3cret" roles="manager-gui"/>
   ```
4. Restarted the serivce and tried to login to tomcat application from the browser. This time it was Successful
