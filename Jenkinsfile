pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'ls'
                sh 'java -jar lib/jenkins-plugin-manager-*.jar --help'
                sh 'java -jar lib/jenkins-plugin-manager-*.jar --war /usr/share/jenkins/jenkins.war --view-all-security-warnings -d /var/tmp/jenkins/ref/plugins'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
