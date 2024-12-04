pipeline {
  agent any
  tools {
    maven 'maven'
    nodejs 'nodejs' // Add NodeJS tool
  }
  stages {
    stage("Clean up") {
      steps {
        deleteDir()
      }
    }

    stage("Clone repo") {
      steps {
        sh "git clone https://github.com/Sawssen19/TP4-Jenkins.git"
      }
    }

    stage("Generate frontend image") {
      steps {
        dir("TP4-Jenkins/angular-app") {
          sh "npm install"
          sh "npm run build"
          sh "docker build -t Sawssen19/angular-app:1.0.0 ."
        }
      }
    }

    stage("Generate backend image") {
      steps {
        dir("TP4-Jenkins/springboot/app") {
          sh "mvn clean install"
          sh "docker build -t Sawssen19/springboot-app:1.0.0 ."
        }
      }
    }

    stage("Run docker compose") {
      steps {
        dir("TP4-Jenkins") {
          sh "docker-compose up -d"
        }
      }
    }
  }
}
