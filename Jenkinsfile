
pipeline {
    agent any
 
    stages {
        stage("Build") {
            steps {
                sh 'cd hello_world'
		sh 'cargo run'
            }
        }
    }
 
    post {
	    always {
        	cleanWs()
    	}
    	success {
	    	slackSend channel: '@yuanjun',
			  color: 'good',
			  message: "The pipeline ${currentBuild.fullDisplayName} completed successfully. Grab the generated builds at ${env.BUILD_URL}"
	    } 
	    failure {
	    	slackSend channel: '@yuanjun',
			  color: 'danger', 
			  message: "The pipeline ${currentBuild.fullDisplayName} failed at ${env.BUILD_URL}"
	    }
    }
}
