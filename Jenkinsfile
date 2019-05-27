pipeline {
	agent "node-develop"
	stages {
		stage ('build') {
			steps {
                sh "cd /home/ubuntu/workspace"
                sh "docker build -t webapp ."
                
            }
		}
		stage ('deploy') {
            steps{
                sh "docker stop"
                sh "docker run -d -p 5000:80 --rm --name webapp webapp"
            }

	}
}
}