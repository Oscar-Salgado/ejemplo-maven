pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                        bat "./mvnw.cmd clean compile -e"
                    
                }
                
            }
        }
        stage('SonarQube') {
            steps {
                script {
					def scannerHome = tool 'sonar-scanner';
					withSonarQubeEnv('sonarqube-server') { 
					bat "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Sonarqube-jenkins -Dsonar.projectBaseDir=c:/repo/ejemplo-maven/ -Dsonar.sources=src -Dsonar.java.binaries=build" 
					}                    
                }
                
            }
        }
        stage('Test') {
            steps {
                script {
                        bat "./mvnw.cmd clean test -e"
                    
                }
                
            }
        }
        stage('Jar') {
            steps {
                script {
                        bat "./mvnw.cmd clean package -e"
                    
                }
                
            }
        }
        stage('Run') {
            steps {
                script {
						bat "start /min mvnw.cmd spring-boot:run &"
						sleep 30
                                           
                }
                
            }
        }
    }
}