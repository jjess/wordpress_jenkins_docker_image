pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub_jjjesss')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t jjess/wordpress_develop:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push jjjesss/wordpress_develop:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
