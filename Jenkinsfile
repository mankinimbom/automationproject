pipeline{
    agent{
        node{
            label 'built-in'
        }
    }
    stages{
        stage('gitcheckout'){
            steps{
                git 'https://github.com/mankinimbom/maven.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('test'){
            steps{
                 git 'https://github.com/mankinimbom/testingproject.git'
                 sh 'java -jar /var/lib/jenkins/workspace/mycriptedpipelin/testing.jar'
            }
        }
        stage('deploytouat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://4.227.254.138:8083')], contextPath: 'uatapp', war: '**/*.war'
            }
        }
        stage('deploytoprod'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://4.227.254.138:8083')], contextPath: '123app', war: '**/*.war'
            }
        }
    }
}
