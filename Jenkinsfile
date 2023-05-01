pipeline {
	agent any
		stages {
		stage ('build && SonarQube analysis') {
			steps {
                        withSonarQubeEnv('my_sonarqube') {
				sh 'mvn clean install -DskipTests sonar:sonar'
			}
		
		}
		stage ('test') {
			steps {
				sh 'mvn test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.*xml'
				}
			}
		}
		stage ('run') {
			steps {
				sh './scripts/deliver.sh'
			}
		
		}
	}
}
