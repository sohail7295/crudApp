pipeline {
    agent any
    
        stages {
            stage('GitPull'){
                steps{
                    git 'https://github.com/dineshp4/crudApp'
                }
            
            }
            stage('Build') {
                steps {
                    sh 'mvn -Dmaven.test.failure.ignore=true clean package'
                    //sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
                    }
               
            }
            stage ('Nexus') {
                steps {
                    nexusArtifactUploader artifacts: [[artifactId: 'crudApp', classifier: '', file: 'target/crudApp.war', type: 'war']], credentialsId: 'nexus', groupId: 'Central', nexusUrl: '18.188.157.192:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'releases', version: '${BUILD_NUMBER}'
                }
            }
            stage ('Docker') {
                steps {
                    sh 'wget http://18.188.157.192:8081/nexus/repository/releases/Central/crudApp/${BUILD_NUMBER}/crudApp-${BUILD_NUMBER}.war -O crudApp.war'
                    sh 'docker build -t crudapp:${BUILD_NUMBER} .'
                    sh 'rm -rf crud*'
                    sh 'docker run -dit -p 8081:8080 --name crudapp.${BUILD_NUMBER} crudapp:${BUILD_NUMBER}'
                }
            }
        }
}
