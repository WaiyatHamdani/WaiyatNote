# Jenkins and DevOps Notes

## table content
- [DevOps Lifecycle](#devops-lifecycle)
- [Role Devops](#role-devops)
- [Install Jenkins Ubuntu](#install-jenkins-ubuntu)
- [Build Script Example](#build-script-example)
- [Test Script Example](#test-script-example)
- [Deployment Script Example](#deployment-script-example)
- [SCM](#scm)

## DevOps Lifecycle
1) Plan
    - Planning the project, defining requirements, and setting goals.
    - tools: Tools: Jira, Trello
2) Code
    - Writing the application code.
    - Tools: Git, GitHub, GitLab, Bitbucket
3) Build
    - Compiling and building the application from the source code.
4) Test
    - Running automated tests on the code to ensure it works as expected.
    - tools:  JUnit, Selenium, and others to automate testing.
5) Release
    - Releasing the software to the staging or production environment.
6) Deploy
    - Deploying the application in production.
    - Jenkins can automate deployment to servers using tools like Kubernetes, Docker, AWS, or traditional web servers
7) Operate
    - Monitoring the application in production to ensure it’s running correctly.
8) Monitor
    - Collecting feedback and analyzing performance to improve the application.
![CICD](../../img/CI-CD.png)
example devops jenkin file:
```bash
pipeline {
    agent any

    stages {
        stage('Code') {
            steps {
                git 'https://github.com/your-repo.git'  # Fetching the latest code
            }
        }
        stage('Build') {
            steps {
                sh './build-script.sh'  # Running build script
            }
        }
        stage('Test') {
            steps {
                sh './run-tests.sh'  # Running tests
            }
        }
        stage('Deploy') {
            steps {
                sh './deploy-to-production.sh'  # Deploying to production
            }
        }
    }
}
```


## Role Devops
1) Continuous Integration (CI): Automatically integrates and tests code changes for consistency.
2) Continuous Delivery (CD): Automatically deploys code to multiple environments for production readiness.
3) Automation: automates repetitive tasks such as code building, testing, and deployment. This reduces manual errors, ensures consistency, and speeds up the release process.

## Install Jenkins Ubuntu
make sure you already habe java jdk  if not : sudo apt install -y openjdk-11-jdk , then follow step by step:
1) Add the Jenkins Repository 
To install the latest stable version of Jenkins, you need to add the Jenkins repository to your system:
```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```
2) Install Jenkins
Once the repository is added, run the following commands to install Jenkins:
```bash
sudo apt update
sudo apt install jenkins
```
3) Start and Enable Jenkins Service
After installation, start the Jenkins service and enable it to start on boot:
```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
4) Adjust Firewall
this part is necessary !! 
If you are running a firewall, you need to allow traffic on port 8080 (the default Jenkins port):
```bash
sudo ufw allow 8080
sudo ufw reload
```
5) Access Jenkins
Jenkins runs on port 8080. You can access Jenkins using your web browser:
```bash
http://your-server-ip:8080
```
6) unlock jenkins 
During the first startup, Jenkins will ask you for an initial administrator password. You can find this password in the following file:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
after unlocking they will install a couple plugin

7) Then create Admin-user




## Build Script Example
./build-script.sh
This script is responsible for compiling the source code. If you're using a Java project, you might use Maven
- example Maven: 
```bash
#!/bin/bash

echo "Building the project..."
mvn clean install

if [ $? -eq 0 ]; then
    echo "Build successful!"
else
    echo "Build failed!"
    exit 1
fi
```



## Test Script Example
./run-tests.sh
This script is responsible for running unit tests after the build is successful Using maven as example:
```bash
#!/bin/bash

echo "Running tests..."
mvn test

if [ $? -eq 0 ]; then
    echo "All tests passed!"
else
    echo "Tests failed!"
    exit 1
fi
```

## Deployment Script Example
This script is responsible for deploying the application to the production environment. Using Docker As example
```bash
#!/bin/bash

echo "Deploying the application..."

# Stop and remove the current running container
docker stop my_app_container
docker rm my_app_container

# Remove the old image
docker rmi my_app_image

# Build a new Docker image
docker build -t my_app_image .

# Run the new container
docker run -d --name my_app_container -p 8080:8080 my_app_image

if [ $? -eq 0 ]; then
    echo "Application deployed successfully!"
else
    echo "Deployment failed!"
    exit 1
fi
```




## SCM 
track changes in source code management (SCM), you typically use a version control system like Git.
Example like below:
```bash
stage('Checkout') {
        steps {
                // Checkout code from the repository
                checkout scm

                // Print out the details of the latest commit
                script {
                    def changeLog = currentBuild.changeSets
                        if (changeLog) {
                            echo "Changes detected in the repository:"
                                for (change in changeLog) {
                                    for (entry in change.items) {
                                        echo "Commit ID: ${entry.commitId}"
                                        echo "Author: ${entry.author}"
                                        echo "Message: ${entry.msg}"
                                    }
                                }
                        } else {
                            echo "No changes detected."
                        }
                }
        }
}
```


