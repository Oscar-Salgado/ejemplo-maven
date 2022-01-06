pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                        sh "./mvnw.cmd clean compile -e"
                }
                
            }
        }
        stage('Test') {
            steps {
                script {
                        sh "./mvnw.cmd clean test -e"
                 }
                
            }
        }
        stage('Jar') {
            steps {
                script {
                        sh "./mvnw.cmd clean package -e" 
                }
                
            }
        }
        stage('Run') {
            steps {
                script {
                        sh "nohup bash mvnw spring-boot:run &" 
						sleep 20
                }
                
            }
        }
        stage('TestApp') {
            steps {
                script {
                        sh "curl -X GET 'http://localhost:8080/rest/mscovid/test?msg=testing'"
                }
                
            }
        }
    }
}