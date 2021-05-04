pipeline {
    agent any
    stages {
        stage('Build'){
            steps{
		sh 'ls'

            }
	}
	stage('Test'){
	    steps{
                sh 'ls'
	    }
 	}
    }
    post {
    failure {
        mail to: 'emroz@student.agh.edu.pl',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
    success {
            echo 'I succeeded :D'
    }
}
}