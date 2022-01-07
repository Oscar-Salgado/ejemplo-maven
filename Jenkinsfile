pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
					sh "./mvnw clean compile -e"
					 
                }
                
            }
        }
        stage('Test') {
            steps {
                script {
					sh "./mvnw clean test -e"
					 
                }
                
            }
        }
        stage('Jar') {
            steps {
                script {
					sh "./mvnw clean package -e"
					 
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
    }
}