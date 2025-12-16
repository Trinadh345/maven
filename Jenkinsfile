pipeline{
    agent any
    stages{
        stage('Download'){
            steps{
                git 'https://github.com/Trinadh345/maven.git'
            }
        }
         stage('Build'){
            steps{
               sh 'mvn package'
            }
        }
         stage('Depoly'){
            steps{
              sh 'scp /var/lib/jenkins/workspace/developement/webapp/target/webapp.war ubuntu@172.31.64.172:/var/lib/tomcat10/webapps/testapp.war'
            }
        }
         stage('Test'){
            steps{
             git 'https://github.com/Trinadh345/functional-testing.git'
             sh 'java -jar /var/lib/jenkins/workspace/developement/testing.jar'
            }
        } 
          stage('Delivery'){
            steps{
                 deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '6a49419f-26e5-4d21-9fb2-070d350eac8b', path: '', url: 'http://172.31.76.18:8080')], contextPath: 'prodapp', war: '**/*.war'

            }
        }
    }
}
