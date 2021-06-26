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
                sh 'ls'
                sh 'java -jar lib/jenkins-plugin-manager-*.jar --help'
                sh 'sudo yum list | grep rclone'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
