pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
            stage('GitPull'){
                steps{
                    git 'https://github.com/sohail7295/crudApp'
                }
            
            }
            stage ('Run Build') {
                steps {
                     sh 'mvn -Dmaven.test.failure.ignore=true clean package'
                      }
             }

            }
           stage ('TomcatRestart') {
                steps {
                    sh "sudo sh /home/ec2-user/apache-tomcat-9.0.14/bin/catalina.sh stop"
                    sh "sudo sh /home/ec2-user/apache-tomcat-9.0.14/bin/catalina.sh start"
                       }
            }
        }
}
