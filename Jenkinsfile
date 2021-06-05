pipeline {
	agent any
	stages {
		stage('Checkout') {
			steps {
					git 'https://github.com/iamdevopstrainer/DevOpsClassCodes'
				}
		}

		stage('Compile')
		{
			steps
			{
				sh 'mvn compile'
			}
		}

		stage('Test')
		{
			steps
			{
				sh 'mvn test'
			}
		}

		stage('Build') {
			steps {
					dir('') {
					sh 'mvn -B -V -U -e clean package'
				}
			}
		}

		stage('Email') {
			steps {
					emailext attachLog: true, body: 'The status of the build can be obtained from the build log attached', subject: 'STATUS: $PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'iamdevopstrainer@gmail.com'
				}
		}
	}	
}
