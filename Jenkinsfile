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
        sh "${mvnHome}/bin/mvn clean package"
      }
    }
  }
}
