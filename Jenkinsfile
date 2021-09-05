pipeline {
    agent any

    tools {
       maven "M3"
    }

    stages {
        stage('Build') {
            steps {                
                git 'https://github.com/wallacerlima/alunoapp.git'       
                sh "mvn clean package"
            }
        }
        
        stage('Deploy n0') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-deployer', path: '', url: 'http://ec2-18-228-235-159.sa-east-1.compute.amazonaws.com:8080/')], contextPath: 'alunoapp', war: 'target/alunoapp.war'
            }
        }
        
        stage('Deploy n1') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-deployer', path: '', url: 'http://ec2-18-229-124-69.sa-east-1.compute.amazonaws.com:8080/')], contextPath: 'alunoapp', war: 'target/alunoapp.war'
            }
        }
        
    }
}
