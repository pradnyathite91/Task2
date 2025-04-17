# 🚀 Task 2: Jenkins CI/CD Pipeline for Application Deployment

This project demonstrates how to set up a basic **CI/CD pipeline using Jenkins** to automate building and deploying an application using Docker.

---

## 🎯 Objective

Automate the process of building, testing, and deploying a simple application using a Jenkins pipeline.

---

## 🛠️ Tools & Technologies

- 🧩 **Jenkins**
- 🐳 **Docker**
- 💻 GitHub (for code commits and triggers)

---

## 📂 Project Structure

. ├── Jenkinsfile # Jenkins pipeline definition ├── Dockerfile # Docker image instructions ├── app/ # Simple application directory │ └── index.js # Sample Node.js application └── package.json # Project dependencies and metadata

bash
Copy
Edit

---

## 🧪 Jenkinsfile Stages

The `Jenkinsfile` includes the following stages:

1. **Build** – Pull source code and build Docker image.
2. **Test** – Run basic test scripts (optional/customizable).
3. **Deploy** – Deploy the Docker container.
---
Example `Jenkinsfile` 

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the Docker image...'
                sh 'docker build -t myapp .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh 'docker run -d -p 3000:3000 --name myapp myapp'
            }
        }
    }
}

---
```
🚦 How It Works
Install Jenkins locally or via a cloud server (e.g., EC2).

Connect GitHub repo to Jenkins.

Create a Jenkins job using a Pipeline type and link it to the repo.

On every commit to the repository, Jenkins:

Pulls the latest code

Builds the Docker image

Runs tests

Deploys the app as a Docker container

🌐 Accessing the App
After deployment, you can access the app via:
```

```bash

http://<your-server-ip>:3000
```
```
✅ Deliverables
✔️ Jenkinsfile with automated build, test, and deploy stages

✔️ Docker-based deployment workflow

✔️ Configured Jenkins job with GitHub integration
```
📌 Notes
Ensure Docker is installed and running on the Jenkins host.

Add Jenkins user to Docker group:

```bash
sudo usermod -aG docker jenkins
Restart Jenkins service after configuration changes.
```
👨‍💻 Author
Pradnya Thite
📧 [pradnyathite91@gmail.com  or (https://github.com/pradnyathite91)]

📎 References
Jenkins Documentation

Docker Documentation

