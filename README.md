B1
Create a Docker image for an application stored in a local repository and run the
application using docker image.
Step1: Download Docker Desktop from the official website:
https://www.docker.com/products/docker-desktop
Install Docker Desktop.
Start Docker Desktop.
Verify installation in terminal / command prompt: docker –version

Step 2: Create a Local Application

Create a folder for the application. Eg: myapp
Inside the folder create a simple Python application. App.py

Step 3: Create a Dockerfile

Inside the same folder create a file named: Dockerfile(without .txt extension)
Add the following content:
FROM python:3.10
WORKDIR /app
COPY . .
CMD ["python","app.py"]

Step 4: Open terminal in the myapp folder.

docker build -t myapp .
Step 5: Verify the docker image
docker images
Step 6: Run the Docker Container
docker run myapp

DevOps Lab Cheat Sheet

Prof. Akshatha M, VVCE
B2: Create and configure Jenkins files for workflow and build of an application
and push the image on docker hub..
Step 1: Build Docker Image from Your Folder

cd your-folder-name
Build the image: docker build -t imagename .

Step 2: Add a Tag:
docker tag imagename yourdockerhubusername/imagename:tagname
eg: docker tag myapp akshatha123/myapp:v1

Step 3: Login to Docker Hub
Step 4: Push Image to Docker Hub
docker push yourdockerhubusername/imagename:tagname
eg: docker push akshatha123/myapp:v1

Step 5: Verify on Docker Hub
Step 6: Push the code to Github

git init
git add .
git commit -m "Initial commit"

git remote add origin https://github.com/your-
username/docker_demo.git

git push -u origin main

Step 7: Add Docker Hub Credentials in Jenkins

Open Jenkins
Manage Jenkins → Credentials → Configure Credentials
Add:
Kind: Username & Password
ID: dockerhub-creds
Username: your Docker Hub username
Password: Docker Hub Access Token
How to Check Docker Access Token

DevOps Lab Cheat Sheet

Prof. Akshatha M, VVCE

Step 1: Open Security Settings
Login to Docker Hub
Click your profile (top right)
Go to:
Account Settings → Security
Open Access Tokens

In command prompt:
echo YOUR_TOKEN | docker login -u your-username --password-stdin

Step 8: Create Jenkins Pipeline Job
Jenkins Dashboard → New Item
Select Pipeline
Configure:
Pipeline → Pipeline script from SCM
SCM → Git
Repo URL → your GitHub repo
Script Path → Jenkinsfile

Step 9: Build Now (manual)

Docker Automation using Webhook
Start by creating a new empty repository
Step 1: Required Background Services (One-Time Setup)
Jenkins
http://localhost:8080
Docker Desktop
Must be running in background
ngrok
ngrok http 8080
Step 2: Set up the Webhook
Step 3: Jenkins Job Config

GitHub hook trigger for GITScm polling

Step 4: Push the code to GitHub
Jenkins should automatically build, else check the plugins
