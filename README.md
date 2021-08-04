# jenkins-demo
Jenkins CI demo for Managing Plugins

Jenkins Plugin Manager Tool
See https://github.com/jenkinsci/plugin-installation-manager-tool

Usage:

Login to the Jenkins Controller (Master) host 
Pull down the latest Jenkins Plugins using the Jenkins CLI

```
java -jar lib/jenkins-plugin-manager-*.jar --help
java -jar lib/jenkins-plugin-manager-*.jar --war $JENKINS_HOME/jenkins.war --list
```
java -jar jenkins-plugin-manager-*.jar --war /usr/lib/jenkins/jenkins.war --plugin-file /opt/jenkins-plugins/plugins.txt --plugins delivery-pipeline-plugin:1.3.2 deployit-plugin

Alternatively you can also use maven:
mvn clean install 
java -jar plugin-management-cli/target/jenkins-plugin-manager-*.jar --war /file/path/jenkins.war --plugin-file /file/path/plugins.txt --plugins delivery-pipeline-plugin:1.3.2 deployit-plugin

Jenkins Plugin Manager Tool
See https://github.com/jenkinsci/plugin-installation-manager-tool

Usage:

java -jar lib/jenkins-plugin-manager-*.jar --help
java -jar lib/jenkins-plugin-manager-*.jar
sudo java -jar lib/jenkins-plugin-manager-*.jar --war /usr/lib/jenkins/jenkins.war --list > plugins.out

Example Jenkinsfile:


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
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

Artifactory repo:

wget https://releases.jfrog.io/artifactory/artifactory-pro-rpms/artifactory-pro-rpms.repo -O jfrog-artifactory-pro-rpms.repo;
sudo mv jfrog-artifactory-pro-rpms.repo /etc/yum.repos.d/;
sudo yum update && sudo yum install jfrog-artifactory-pro

Download JFrog CLI:
curl -fL https://getcli.jfrog.io | sh

Jenkins REST API:

curl -X POST \
		--data "<jenkins><install plugin='${name}@latest' /></jenkins>" \
		--header 'Content-Type: text/xml' \
		http://localhost:8080/pluginManager/installNecessaryPlugins

There are multiple ways to list your Jenkins Plugins:

Way 1: Script console(groovy code):
go to http:<Jenkins_URl>/script
Run below command:

Jenkins.instance.pluginManager.plugins.each{
  plugin ->
    println ("${plugin.getShortName()}")
}
Way 2: Command CLI
Download command-CLI jar from : http://<Jenkins_URL>/jnlpJars/jenkins-cli.jar
Run below command:
java -jar jenkins-cli.jar -s http://<JENKINS_URL>/ list-plugins --username "<Jenkins_USERNAME>" --password "<Jenkins_Password>"

Way 3: Jenkins Python API

import jenkins
import json
server = jenkins.Jenkins('<jenkinsurl>', username='<Jenkins_user>', password='<Jenkins_User_password>')
all_plugins_info=server.get_plugins_info()
for each_plugin in all_plugins_info:
    print each_plugin['shortName']


$ curl -u "<admin>:<pwd>" 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'
Result:
Jenkins-Crumb:4b4f34e04e4ffe60c2ca15d6fc8e50f3e8041061fe5d82742169077ad6d98036
