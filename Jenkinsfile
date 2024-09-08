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

                script {
                    // Build the Docker image
                    sh "docker build -t rajeshtalla0209/votingapp-vote:${VERSION} ."
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Run the Docker container and expose port 80
                    // Note: The '-it' flag is generally used for interactive terminal, which might not be needed here
                    // It’s better to run in detached mode with '-d' if it’s meant for background services
                    sh "docker run -d -p 80:80 rajeshtalla0209/votingapp-vote:${VERSION}"
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Tag the image (this step is optional if the image is already tagged correctly)
                    sh "docker tag rajeshtalla0209/votingapp-vote:${VERSION} rajeshtalla0209/votingapp-vote:${VERSION}"

                    // Push the image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_cred') {
                        sh "docker push rajeshtalla0209/votingapp-vote:${VERSION}"
                    }
                }
            }
        }
    }
}
