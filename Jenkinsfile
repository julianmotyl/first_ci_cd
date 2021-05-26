pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'mvn -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('SonarQube analysis') {
           steps {
            	withSonarQubeEnv('Sonar Cloud') {
                	bat 'mvn sonar:sonar'
              	}

           }
        }
    }
}
