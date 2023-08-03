# Configure Git pulgin on Jenkins
Git is the version control tool I have used.I have pulled the code from git repo using jenkins through installing git plugin and by configuring it. 


#### Prerequisites
1. Jenkins server (amazon-linux-instance)

#### Install Git on Jenkins server
1. Install git packages on jenkins server
   ```sh
   yum install git -y
   ```

#### Setup Git on jenkins console
- Install git plugin without restart  
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `github`

- Configure git path
  - `Manage Jenkins` > `Global Tool Configuration` >`git`
