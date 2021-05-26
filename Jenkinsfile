pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage("SonarQube analysis") {
        	steps {
            	withSonarQubeEnv('SonarCloud') {
                	sh 'mvn sonar:sonar'
              	}
            }
        }
    }
}
