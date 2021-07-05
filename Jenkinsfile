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
                sh 'java -jar lib/jenkins-plugin-manager-*.jar --war /usr/local/opt/jenkins/libexec/jenkins.war --plugin-file latest/plugins.txt -d /var/tmp/jenkins/ref/plugins'
                sh '/var/tmp/jenkins/ref/plugins'
            }
        }
    }
}
