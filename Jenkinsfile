pipeline {
    agent {}
    stages {
        stage('Build'){
            steps{
                sh 'curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
		sh 'chmod +x /usr/local/bin/docker-compose'
		sh 'git pull origin master'
		sh 'docker-compose up -d'

            }
	}
	stage('Test'){
            
            steps{
                sh 'code/wait.sh server:1234 -- echo READY && node code/client.js'
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