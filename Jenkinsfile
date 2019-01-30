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
  }
}
