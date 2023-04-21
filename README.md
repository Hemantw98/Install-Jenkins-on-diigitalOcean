## Install-Jenkins-on-diigitalOcean
### Technologies used:
Jenkins, Docker, DigitalOcean, Linux

### Project Description:
Create an Ubuntu server on DigitalOcean
Set up and run Jenkins as Docker container
Initialize Jenkins

### Here are the complete steps to install Jenkins on a DigitalOcean droplet:

### Prerequisites:

A DigitalOcean account with a running Ubuntu droplet.
SSH access to the Ubuntu droplet.

Step 1: Update System Packages
Connect to your Ubuntu droplet via SSH and update the system packages to their latest versions:

      sudo apt update
    sudo apt upgrade -y
    
Step 2: Install Java Development Kit (JDK)
Jenkins requires Java to run. Install OpenJDK on your Ubuntu droplet:

    sudo apt install openjdk-11-jdk -y

Step 3: Install Jenkins
Add the Jenkins repository to apt's sources list and import the Jenkins GPG key:

        wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    
 Update apt's package index and install Jenkins:
 
     sudo apt update
    sudo apt install jenkins -y

Step 4: Start Jenkins Service
Start the Jenkins service and enable it to start on boot:

    sudo systemctl start jenkins
    sudo systemctl enable jenkins
    
Step 5: Configure Firewall
If you have a firewall enabled on your droplet, allow incoming traffic on port 8080 for Jenkins:

    sudo ufw allow 8080
    
Step 6: Access Jenkins Web Interface
Open a web browser and navigate to http://<your_droplet_ip>:8080. You'll see the Jenkins Unlock Jenkins page. Retrieve the Jenkins initial admin password from the server:

    sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Copy the password and paste it in the Unlock Jenkins page to unlock Jenkins.

Step 7: Install Plugins
In the Jenkins setup wizard, select "Install suggested plugins" to install the recommended plugins. This may take a few minutes.

Step 8: Create Jenkins User
Create an admin user and provide the required details like username, password, full name, and email address.

Step 9: Finish Setup
Complete the Jenkins setup wizard by providing the URL for your Jenkins instance (e.g., http://<your_droplet_ip>:8080) and clicking "Save & Finish".

That's it! Jenkins is now installed on your DigitalOcean droplet. You can start using Jenkins to set up your build pipelines, automate your CI/CD workflows, and more.








