pipeline {
    agent any

    environment {
        VERSION = '1'
    }

    stages {
        stage('Build') {
            steps {
                // Checkout the code
                git 'https://github.com/RKDevops1234/votingapp-vote.git'

                // Build the Docker image
                sh "docker build -t rajeshtalla0209/votingapp-vote:${VERSION} ."
            }
        }

        stage('Run') {
            steps {
                // Run the Docker container and expose port 80
                sh "docker run -p 80:80 -it rajeshtalla0209/votingapp-vote:${VERSION}"
            }
        }

        stage('Push to Docker Hub') {
            steps {
                // Tag the image with your Docker Hub username and repository name
                sh "docker tag rajeshtalla0209/votingapp-vote:${VERSION} rajeshtalla0209/votingapp-vote:${VERSION}"
                docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_cred') {
                    // Push the image to Docker Hub
                    sh "docker push rajeshtalla0209/votingapp-vote:${VERSION}"
                }
            }
        }
    }
}