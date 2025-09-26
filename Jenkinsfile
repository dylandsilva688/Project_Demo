pipeline {
    agent any
    triggers {
  cron 'H/5 * * * *'
}

    tools{
        maven 'apache-maven-3.9.5'
    }
    options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
}


    stages {
        stage('Clone the repository') {
            steps {
               git credentialsId: 'Github_username_password', url: 'https://github.com/dylandsilva688/Project_Demo.git'
            }
        }


        stage('Build the maven code') {
            steps {
            dir('App01'){
            sh 'mvn clean install'
                        }
                 }
    }

stage('Deploy to tomcat') {
            steps {
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '735a5106-4896-4c24-868a-56aaf0cd291c', path: '', url: 'http://localhost:8181')], contextPath: null, war: '**/*.war'
                 }
    }
}
}
