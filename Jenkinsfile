pipeline {
  agent any
  stages {
    stage ('checkout code') {
      steps {
        git 'https://github.com/sohail7295/crudApp'
      }
   }
    stage ('Run Build') {
      steps {
        def mvnHome = tool 'M3'
        sh "${mvnHome}/bin/mvn clean package"
      }
    }
  }
}
