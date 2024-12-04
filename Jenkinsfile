pipeline {
  agent any
  tools {
    maven 'maven'
    }
  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
        }
      }

    stage ("Clone repo"){
      steps {
        sh "git clone https://github.com/Sawssen19/TP4-Jenkins.git"
        }
      }


    stage ("Generate frontend image"){
      steps {
        dir("TP4-Jenkins/angular-app"){
          sh "mvn clean install"
          sh "docker build -t angular-app ."
          }
        }
      }

    stage ("Generate backend image"){
      steps {
        dir("TP4-Jenkins/springboot/app"){
          sh "mvn clean install"
          sh "docker build -t springboot-app ."
          }
        }
      }


    stage ("Run docker compose"){
      steps {
        dir("TP4-Jenkins"){
          sh "docker-compose up -d"
          }
        }
      }
    }
  }
