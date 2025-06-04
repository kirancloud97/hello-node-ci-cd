# Hello Node CI/CD Project

A simple Node.js application demonstrating a CI/CD pipeline using Jenkins, Docker, and GitHub.
Setup Instructions

 1. Prerequisites

- EC2 instance (Ubuntu-based)
- Jenkins (with required plugins):
  - Git
  - Docker Pipeline
  - Pipeline
  - GitHub Integration
- Docker
- Git
- A GitHub repository https://github.com/kirancloud97/hello-node-ci-cd/tree/master
- A Docker Hub account with a repository created https://hub.docker.com/r/kirancloud97/hello-node

 2. Jenkins Configuration
Install Required Packages

Jenkins Setup
Create a new Jenkins Pipeline project hello-node-pipeline.

Used the following GitHub repository for the pipeline:
https://github.com/kirancloud97/hello-node-ci-cd.git


Add Docker Hub Credentials In Jenkins
Running the Jenkins Pipeline
any changes to the master branch it will trigger the jenkins pipeline.

Jenkins will automatically Clone the repository ,Build a Docker image, Push the image to Docker Hub

Deploy the container 

GitHub Webhook Setup 
In GitHub repo Go to Settings → Webhooks → Add Webhook
Payload URL: http://18.220.216.248:8080/github-webhook/


Assumptions and Notes

Node.js app listens on port 3000
Jenkins and Docker are installed on the same EC2 instance
Docker Hub is used as the image registry
Jenkins runs on port 8080

App entry point is app.js and dependencies are listed in package.json

Example Output
http://18.220.216.248:3000/
**Hello World**
