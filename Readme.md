In this assessment for the 1st question I had 2 options:
1. manually installing Jenkins
2. docker pull

I chose option 2 "docker pull jenkins/jenkins:jdk21" post this Jenkins was properly running

For installing plugins i had 3 options:
1. manually
2. via CLI
3. download via google > go to docker container where Jenkins is running > find the plugins folder in Jenkins and paste it there

For this I choose option 1 

I did setup Git credentials 

For 2nd question I created Jenkins pipeline for pulling code from github and fixing the credentials in pipeline post that 3 stages were created in pipeline:
1. pull code from Github
2. for testing I used Maven project and mvn test
3. Created JUnit stage for integrated testing
4. Stored output file in local system

For 3rd Question I implemented github webhook for automatic triggering the Jenkins pipeline post repo changes

For 4th question I created pipelines for CD then in this pipeline:
1. I selected AWS deployment then I mentioned AWS credentials
2. copiied artifact from CI pipeline
3. using Jenkins pipeline created AWS EC2 Instance
4. then application was deployed in EC2 Instance
5. new pipeline was created for DB
6. then S3 bucket was created to store daily DB backup
