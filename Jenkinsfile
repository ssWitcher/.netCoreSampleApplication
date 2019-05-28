pipeline {
	agent {
    node {
        label 'node-develop'
        customWorkspace '/home/ubuntu/workspace'
    }
}
	stages {
		stage ('build') {
			steps {
                sh "cd /home/ubuntu/workspace"
                sh "docker build -t webapp ."
                sh "\$(aws ecr get-login --no-include-email --region ap-south-1)"
                sh "docker tag webapp:latest 895763823661.dkr.ecr.ap-south-1.amazonaws.com/webapp:latest"
                sh "docker push 895763823661.dkr.ecr.ap-south-1.amazonaws.com/webapp:latest"
                
            }
		}
		stage ('deploy') {
            steps{
                sh "docker rm -f webapp"
                sh "docker run -d -p 5000:80 --rm --name webapp webapp"
            }

	}
}
}