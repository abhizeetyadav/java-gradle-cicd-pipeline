# Java Web App CI/CD Pipeline with Jenkins

This project demonstrates a complete CI/CD pipeline setup using Jenkins for a Java web application built with Gradle and deployed to an Apache Tomcat server.

## 📌 Project Overview

The pipeline performs the following tasks:

1. **Clones** the source code from a GitHub repository.
2. **Builds** the Java web application using Gradle.
3. **Verifies** the generated WAR file.
4. **Deploys** the WAR file to a local Apache Tomcat server.
5. **Restarts** the Tomcat server to apply the latest deployment.

## 🚀 Tools & Technologies

- **Jenkins** – Automation server to run CI/CD pipeline
- **Gradle** – Build automation tool for Java
- **Git** – Version control system
- **Apache Tomcat** – Web server for deploying Java web apps
- **Shell Scripts** – For build and deployment steps

## 🛠️ Jenkins Pipeline Configuration

The Jenkins pipeline is written in Declarative syntax and includes the following stages:

- **Checkout Code**
- **Build with Gradle**
- **Verify WAR File**
- **Deploy WAR to Tomcat**

### Environment Variables Used:

| Variable            | Description                             |
|---------------------|-----------------------------------------|
| `GIT_REPO`          | URL of the GitHub repository            |
| `ROOT_WAR_LOCATION` | Tomcat deployment directory             |
| `LOCAL_WAR_FILE`    | Location of the WAR file after build    |
| `TOMCAT_BIN_DIR`    | Path to Tomcat's bin folder             |
| `GRADLE_PATH`       | Path to the Gradle binary               |

## 🔧 Prerequisites

Make sure the following are installed and configured:

- Jenkins installed and running
- Jenkins user has `sudo` privileges (or adjust scripts accordingly)
- Apache Tomcat installed in `/opt/tomcat`
- Gradle installed at `/usr/local/gradle/gradle-8.11/`
- GitHub repository accessible (public or via credentials if private)

## 📂 Project Structure

java-gradle-cicd/
├── build.gradle
├── settings.gradle
├── Jenkinsfile
├── src/
│   └── main/
│       ├── java/
│       │   └── com/example/HelloServlet.java
│       └── webapp/WEB-INF/web.xml
