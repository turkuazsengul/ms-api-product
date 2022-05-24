pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {

		stage('Build') {

			steps {
			    sh 'mvn -Dmaven.test.skip install'
				sh 'docker build -f Dockerfile -t turkuazsengul/ms-api-product:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push turkuazsengul/ms-api-product:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}