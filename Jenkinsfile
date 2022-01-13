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
			def scannerHome = tool 'sonar-scanner';
			withSonarQubeEnv('sonarqube-server') { 
			bat "${scannerHome}/bin/sonar-scanner -Dsonar.sonar.projectKey=Sonarqube-jenkins -Dsonar.sonar.projectBaseDir=c:/repo/ejemplo-maven/ -Dsonar.sonar.sources=src -Dsonar.sonar.java.binaries=build" 
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