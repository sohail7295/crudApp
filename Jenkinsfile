pipeline {
  agent any
  tools {
        maven 'M3'
    }
  stages {
    stage ('checkout code') {
      steps {
        git 'https://github.com/sohail7295/crudApp'
      }
   }
    stage ('Run Build') {
      steps {
        sh "/opt/apache-maven-3.3.9/bin/mvn clean package"
      }
    }
    stage ('Nexus') {
      steps {
      nexusArtifactUploader artifacts: [[artifactId: 'crudApp', classifier: '', file: 'target/crudApp.war', type: 'war']], credentialsId: 'nexus', groupId: 'Central', nexusUrl: '192.168.56.103:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'releases', version: '2.2'
      }
    }
    stage ('Copy to tomcat') {
      steps {
      sh "wget http://192.168.56.103:8081/nexus/service/local/repositories/releases/content/Central/crudApp/2.2/crudApp-2.2.war -O /opt/apache-tomcat-9.0.14/webapps/crudApp.war"
      }
    }
  }
}
