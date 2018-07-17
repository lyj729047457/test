
pipeline {
    agent any
 
    stages {
        stage("Build") {
            steps {
		sh 'cargo run'
            }
        }
    }
 
    post {
	    always {
        	cleanWs()
    	    }
    	    success {
	    	slackSend baseUrl: 'https://aionsh.slack.com/services/hooks/jenkins-ci/', 
			channel: '@yuanjun', 
			color: 'good', 
			message: 'The pipeline ${currentBuild.fullDisplayName} completed successfully. Grab the generated builds at ${env.BUILD_URL}', 
			teamDomain: 'aionsh', 
			token: 'wG5SRL6unTjd9o4XS90MfHZT'

	    } 
	    failure {
	    	slackSend baseUrl: 'https://aionsh.slack.com/services/hooks/jenkins-ci/', 
		        channel: '@yuanjun',
			color: 'danger', 
			message: "The pipeline ${currentBuild.fullDisplayName} failed at ${env.BUILD_URL}",
			teamDomain: 'aionsh', 
			token: 'wG5SRL6unTjd9o4XS90MfHZT'
				
	    }
    }
}
