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
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '6a49419f-26e5-4d21-9fb2-070d350eac8b', path: '', url: 'http://172.31.64.172:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
         stage('Test'){
            steps{
             git 'https://github.com/Trinadh345/FunctionalTesting.git'
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
