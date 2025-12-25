pipeline {
  agent any

  stages {
    stage('Git checkout scm') {
      steps {
        git branch: 'main', url: 'https://github.com/Hema8368/webemployee.git'
      }
    }

    stage('Compile the code') {
      steps { sh 'mvn -B clean compile' }
    }

    stage('Testing the code') {
      steps { sh 'mvn -B test' }
    }

    stage('Package the code') {
      steps { sh 'mvn -B package' }
    }

    stage('Deploy to the tomcat') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcatcred', url: 'http://13.219.255.14:8080')],
               war: 'target/*.war',
               contextPath: '/employee-details'
      }
    }
  }
}
