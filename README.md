# Discover Dollar – MEAN Stack CI/CD Project

This project implements a CI/CD pipeline using Jenkins, Docker, and AWS EC2 for a full-stack MEAN (MongoDB, Express, Angular, Node.js) application.

# Tech Stack

Frontend: Angular + NGINX

Backend: Node.js + Express

Database: MongoDB

CI/CD: Jenkins

Containerization: Docker & Docker Hub

Deployment: AWS EC2 (Ubuntu 22.04)


# Project Architecture

graph TD;
A[GitHub Repo] -->|Push Code| B[Jenkins CI/CD Pipeline];
B --> C[Docker Build & Push];
C --> D[Docker Hub];
D -->|Pull Images| E[AWS EC2];
E --> F[Docker Compose Up];
F --> G[Running Containers];


# Setup Instructions
# Clone Repository
git clone https://github.com/Nitin201/DISCOVER-DOLLAR-ASSIGNMENT.git
cd DISCOVER-DOLLAR-ASSIGNMENT

# Backend Setup
cd backend
npm install
npm start

# Frontend Setup
cd frontend
npm install
ng build --configuration production

# Docker Setup
Build Images
docker build -t nitin241/dd-mean-backend:latest ./backend
docker build -t nitin241/dd-mean-frontend:latest ./frontend

# Run via Docker Compose
docker-compose up -d


# CI/CD Pipeline Overview
Jenkins Stages

Checkout Code – Pulls code from GitHub

Build Docker Images – Builds frontend and backend containers

Push to Docker Hub – Uploads images to Docker Hub

Deploy to EC2 – SSHs into EC2, pulls new images, recreates containers

Post Actions – Prints deployment success and live app URL

# Docker Hub Repositories
  # Image	Link
# Backend	nitin241/dd-mean-backend

# Frontend	nitin241/dd-mean-frontend


# Final Output
# App successfully deployed and accessible at:
# http://3.110.125.61


# CI/CD Execution



[#7.txt](https://github.com/user-attachments/files/23821877/7.txt)
Started by user nitin
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/MEAN-CI-CD-Pipeline
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Checkout Code)
[Pipeline] echo
Checking out code from GitHub...
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/MEAN-CI-CD-Pipeline/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/Nitin201/DISCOVER-DOLLAR-ASSIGNMENT.git # timeout=10
Fetching upstream changes from https://github.com/Nitin201/DISCOVER-DOLLAR-ASSIGNMENT.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/Nitin201/DISCOVER-DOLLAR-ASSIGNMENT.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision de07056b98872f1f2dd7cbe61b4e102b60316659 (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f de07056b98872f1f2dd7cbe61b4e102b60316659 # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D master # timeout=10
 > git checkout -b master de07056b98872f1f2dd7cbe61b4e102b60316659 # timeout=10
Commit message: "added nginx and docker-compose & update frontend and backend dockerfile"
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Docker Images)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
Building Docker images...
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker build -t nitin241/dd-mean-backend:latest ./backend
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 239B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/node:18-alpine
#2 DONE 1.2s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s

#4 [internal] load build context
#4 transferring context: 506B done
#4 DONE 0.0s

#5 [1/5] FROM docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8ca09d9e
#5 resolve docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8ca09d9e 0.0s done
#5 DONE 0.0s

#6 [2/5] WORKDIR /app
#6 CACHED

#7 [3/5] COPY package*.json ./
#7 CACHED

#8 [4/5] RUN npm install --only=production
#8 CACHED

#9 [5/5] COPY . .
#9 CACHED

#10 exporting to image
#10 exporting layers done
#10 exporting manifest sha256:83bca6735851b9d9b9cc72a57103670f0f2af3bf8f8ddd854e8e0b41b705bbf3 done
#10 exporting config sha256:d3767b41ed520f0e63c9d52aee4415049df3cce5013bbb5c64867a0558e1c276 done
#10 exporting attestation manifest sha256:c20531cd3bef558681a21c738af3a0af5fd93c7c7b0b9e1e0760fb40ec954d5b 0.0s done
#10 exporting manifest list sha256:7598f01a9dc1ac2dc9e7e308588f1c181b94977862f890b74d3f35548a20fa76 0.0s done
#10 naming to docker.io/nitin241/dd-mean-backend:latest
#10 naming to docker.io/nitin241/dd-mean-backend:latest done
#10 unpacking to docker.io/nitin241/dd-mean-backend:latest done
#10 DONE 0.1s
[Pipeline] }
[Pipeline] // withEnv
Did you forget the `def` keyword? WorkflowScript seems to be setting a field named backendImage (to a value of type Image) which could lead to memory leaks or other issues.
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker build -t nitin241/dd-mean-frontend:latest ./frontend
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 392B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/nginx:alpine
#2 ...

#3 [internal] load metadata for docker.io/library/node:18-alpine
#3 DONE 0.2s

#2 [internal] load metadata for docker.io/library/nginx:alpine
#2 DONE 1.2s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.0s

#5 [internal] load build context
#5 transferring context: 2.34kB done
#5 DONE 0.0s

#6 [stage-1 1/4] FROM docker.io/library/nginx:alpine@sha256:b3c656d55d7ad751196f21b7fd2e8d4da9cb430e32f646adcf92441b72f82b14
#6 resolve docker.io/library/nginx:alpine@sha256:b3c656d55d7ad751196f21b7fd2e8d4da9cb430e32f646adcf92441b72f82b14 0.0s done
#6 DONE 0.0s

#7 [build 1/6] FROM docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8ca09d9e
#7 resolve docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8ca09d9e 0.0s done
#7 DONE 0.0s

#8 [build 3/6] COPY package*.json ./
#8 CACHED

#9 [build 4/6] RUN npm install
#9 CACHED

#10 [build 5/6] COPY . .
#10 CACHED

#11 [build 6/6] RUN npm run build -- --configuration production
#11 CACHED

#12 [build 2/6] WORKDIR /app
#12 CACHED

#13 [stage-1 2/4] COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html
#13 CACHED

#14 [stage-1 3/4] RUN rm /etc/nginx/conf.d/default.conf
#14 CACHED

#15 [stage-1 4/4] COPY nginx.conf /etc/nginx/conf.d/default.conf
#15 CACHED

#16 exporting to image
#16 exporting layers done
#16 exporting manifest sha256:cb5f93aa8f7d5d1a9e6fb9bc12abd7f08372f315f929a0e348b06ac95ec26e1b done
#16 exporting config sha256:3d2c5636bfa322d6160e35929a63db4b76c35d3dc2e962ddca36e4991b0fcab7 done
#16 exporting attestation manifest sha256:24d88cca0c74451320148bc685dffab182f3e49cc000f697dbd3251fd44eb5a4 0.0s done
#16 exporting manifest list sha256:0893caf4c91c76921138e37454c6edc2f51f41071ab600ffa11468e0812e5b6c
#16 exporting manifest list sha256:0893caf4c91c76921138e37454c6edc2f51f41071ab600ffa11468e0812e5b6c 0.0s done
#16 naming to docker.io/nitin241/dd-mean-frontend:latest done
#16 unpacking to docker.io/nitin241/dd-mean-frontend:latest done
#16 DONE 0.1s
[Pipeline] }
[Pipeline] // withEnv
Did you forget the `def` keyword? WorkflowScript seems to be setting a field named frontendImage (to a value of type Image) which could lead to memory leaks or other issues.
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push to Docker Hub)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
Pushing images to Docker Hub...
[Pipeline] withDockerRegistry
$ docker login -u nitin241 -p ******** https://index.docker.io/v1/
WARNING! Using --password via the CLI is insecure. Use --password-stdin.

WARNING! Your credentials are stored unencrypted in '/var/lib/jenkins/workspace/MEAN-CI-CD-Pipeline@tmp/09e3358f-1ce4-4988-baf0-f9dcacc7994f/config.json'.
Configure a credential helper to remove this warning. See
https://docs.docker.com/go/credential-store/

Login Succeeded
[Pipeline] {
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker tag nitin241/dd-mean-backend:latest nitin241/dd-mean-backend:latest
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker push nitin241/dd-mean-backend:latest
The push refers to repository [docker.io/nitin241/dd-mean-backend]
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
f18232174bc9: Layer already exists
dd71dde834b5: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Waiting
1630ee225b35: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
acb4f52ebad0: Layer already exists
1630ee225b35: Layer already exists
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
dd71dde834b5: Waiting
db5f895d5d1a: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Layer already exists
aaf966aca005: Layer already exists
dd71dde834b5: Layer already exists
db5f895d5d1a: Waiting
1335b456ef9e: Layer already exists
1e5a4c89cee5: Layer already exists
db5f895d5d1a: Pushed
latest: digest: sha256:7598f01a9dc1ac2dc9e7e308588f1c181b94977862f890b74d3f35548a20fa76 size: 856
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker tag nitin241/dd-mean-backend:latest nitin241/dd-mean-backend:v7
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker push nitin241/dd-mean-backend:v7
The push refers to repository [docker.io/nitin241/dd-mean-backend]
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
dd71dde834b5: Layer already exists
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
acb4f52ebad0: Waiting
25ff2da83641: Waiting
1630ee225b35: Layer already exists
aaf966aca005: Waiting
1335b456ef9e: Waiting
1e5a4c89cee5: Layer already exists
acb4f52ebad0: Waiting
25ff2da83641: Waiting
aaf966aca005: Waiting
1335b456ef9e: Waiting
db5f895d5d1a: Waiting
f18232174bc9: Waiting
acb4f52ebad0: Layer already exists
25ff2da83641: Layer already exists
aaf966aca005: Layer already exists
1335b456ef9e: Layer already exists
db5f895d5d1a: Already exists
f18232174bc9: Layer already exists
v7: digest: sha256:7598f01a9dc1ac2dc9e7e308588f1c181b94977862f890b74d3f35548a20fa76 size: 856
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker tag nitin241/dd-mean-frontend:latest nitin241/dd-mean-frontend:latest
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker push nitin241/dd-mean-frontend:latest
The push refers to repository [docker.io/nitin241/dd-mean-frontend]
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
bdabb0d44271: Layer already exists
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Layer already exists
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
04179b1f9da4: Waiting
44cecbe13262: Waiting
3eaba6cd10a3: Waiting
d9a55dab5954: Waiting
ce41c1950f11: Waiting
2d35ebdb57d9: Waiting
194fa24e147d: Waiting
050115e52b4d: Waiting
df413d6ebdc8: Waiting
ff8a36d5502a: Waiting
2d35ebdb57d9: Layer already exists
194fa24e147d: Layer already exists
050115e52b4d: Layer already exists
df413d6ebdc8: Layer already exists
ff8a36d5502a: Layer already exists
04179b1f9da4: Layer already exists
44cecbe13262: Layer already exists
3eaba6cd10a3: Layer already exists
d9a55dab5954: Layer already exists
ce41c1950f11: Waiting
ce41c1950f11: Waiting
ce41c1950f11: Waiting
ce41c1950f11: Pushed
latest: digest: sha256:0893caf4c91c76921138e37454c6edc2f51f41071ab600ffa11468e0812e5b6c size: 856
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker tag nitin241/dd-mean-frontend:latest nitin241/dd-mean-frontend:v7
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] isUnix
[Pipeline] withEnv
[Pipeline] {
[Pipeline] sh
+ docker push nitin241/dd-mean-frontend:v7
The push refers to repository [docker.io/nitin241/dd-mean-frontend]
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
194fa24e147d: Layer already exists
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
ce41c1950f11: Waiting
df413d6ebdc8: Waiting
ce41c1950f11: Already exists
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
bdabb0d44271: Layer already exists
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
3eaba6cd10a3: Waiting
3eaba6cd10a3: Waiting
df413d6ebdc8: Waiting
d9a55dab5954: Waiting
ff8a36d5502a: Waiting
2d35ebdb57d9: Waiting
8f6a6833e95d: Waiting
44cecbe13262: Waiting
050115e52b4d: Waiting
04179b1f9da4: Waiting
050115e52b4d: Layer already exists
04179b1f9da4: Layer already exists
3eaba6cd10a3: Layer already exists
df413d6ebdc8: Layer already exists
d9a55dab5954: Layer already exists
ff8a36d5502a: Layer already exists
2d35ebdb57d9: Layer already exists
8f6a6833e95d: Layer already exists
44cecbe13262: Layer already exists
v7: digest: sha256:0893caf4c91c76921138e37454c6edc2f51f41071ab600ffa11468e0812e5b6c size: 856
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // withDockerRegistry
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Deploy to EC2)
[Pipeline] echo
Deploying to EC2 instance 3.110.125.61...
[Pipeline] sshagent
[ssh-agent] Using credentials ubuntu
$ ssh-agent
SSH_AUTH_SOCK=/tmp/ssh-UgCPgavvol5Y/agent.38608
SSH_AGENT_PID=38611
Running ssh-add (command line suppressed)
Identity added: /var/lib/jenkins/workspace/MEAN-CI-CD-Pipeline@tmp/private_key_3423749463295428205.key (/var/lib/jenkins/workspace/MEAN-CI-CD-Pipeline@tmp/private_key_3423749463295428205.key)
[ssh-agent] Started.
[Pipeline] {
[Pipeline] sh
+ ssh -o StrictHostKeyChecking=no ubuntu@3.110.125.61 
                        cd ~/DISCOVER-DOLLAR-ASSIGNMENT &&
                        git pull || true &&
                        docker compose pull &&
                        docker compose up -d &&
                        docker image prune -f
                        
Already up to date.
time="2025-11-28T10:36:55Z" level=warning msg="/home/ubuntu/DISCOVER-DOLLAR-ASSIGNMENT/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion"
 frontend Pulling 
 mongo Pulling 
 backend Pulling 
 backend Pulled 
 mongo Pulled 
 frontend Pulled 
time="2025-11-28T10:36:57Z" level=warning msg="/home/ubuntu/DISCOVER-DOLLAR-ASSIGNMENT/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion"
 Container dd-mongo  Running
 Container dd-backend  Recreate
 Container dd-backend  Recreated
 Container dd-frontend  Recreate
 Container dd-frontend  Recreated
 Container dd-backend  Starting
 Container dd-backend  Started
 Container dd-frontend  Starting
 Container dd-frontend  Started
Total reclaimed space: 0B
[Pipeline] }
$ ssh-agent -k
unset SSH_AUTH_SOCK;
unset SSH_AGENT_PID;
echo Agent pid 38611 killed;
[ssh-agent] Stopped.
[Pipeline] // sshagent
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Declarative: Post Actions)
[Pipeline] echo
Deployment successful!
[Pipeline] echo
App is live at: http://3.110.125.61
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS



