pipeline {
    agent any

    stages {
        stage('Git checkout scm') {
            steps {
                git 'https://github.com/Hema8368/webemployee.git'
            }
        }
        stage('Compile the code ') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('testing the code') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package the code ') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy to the tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcatcred', path: '', url: 'http://13.219.255.14:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
