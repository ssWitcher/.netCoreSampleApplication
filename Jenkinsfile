pipeline {
	agent {
    node {
        label 'node-prod'
        customWorkspace '/home/ubuntu/workspace'
    }
}
	stages {
		stage ('deploy') {
            steps{
                sh "docker rm -f webapp"
                sh "\$(aws ecr get-login --no-include-email --region ap-south-1)"
                sh "docker pull 895763823661.dkr.ecr.ap-south-1.amazonaws.com/webapp:latest"
                sh "docker run -d -p 5000:80 --rm --name webapp 895763823661.dkr.ecr.ap-south-1.amazonaws.com/webapp:latest"
            }

	}
}
}