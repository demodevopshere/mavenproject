pipeline {
    agent {
        label 'devnode'
    }
    tools {
        maven 'maven3.81'
    }
    stages {
        stage('Get the code') {
            steps {
                git 'https://github.com/demodevopshere/mavenproject'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Approval from release manager') {
             input {
                 message "Approved By ReleaseManager"
             }
        }
        stage('DevDeploy') {
            steps {
                sh 'cp target/JenkinsWar.war /var/lib/tomcat9/webapps'
            }
        }
    }
}
