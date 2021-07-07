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
