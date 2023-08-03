# Install Jenkins on AWS EC2
 Jenkins is an open-source automation server that facilitates continuous integration (CI) and continuous delivery (CD) processes .

### Prerequisites
1. EC2 Instance 
   - With Internet Access
   - Security Group with Port `8080` open for internet (Because jenkins run on this port number)
1. Java 11 should be installed  

## Install Jenkins
1. Got the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ and install
   ```sh
   sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
   amazon-linux-extras install epel 
   amazon-linux-extras install java-openjdk11  
   ```
   ### Start Jenkins
   ```sh
   # Start jenkins service
   service jenkins start
   ```
   ### Accessing Jenkins
   By default jenkins runs at port `8080`, I have acessed jenkins at
   ```sh
   http://SERVER-PUBLIC-IP:8080
   ```
  #### Configure Jenkins
- The default Username is `admin`
- Grab the default password 
- Password Location:`/var/lib/jenkins/secrets/initialAdminPassword`
- Configure `java` path
  - `Manage Jenkins` > `Global Tool Configuration` > `JDK`  
