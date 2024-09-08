pipeline {
    agent any

    environment {
        VERSION = '1'
    }

    stages {
        stage('Build') {
            steps {
                // Checkout the code
                git branch: 'main',
                    credentialsId: 'your-credentials-id',
                    url: 'https://github.com/RKDevops1234/votingapp-vote.git'

                // Print the Git repository information
                sh 'git remote -v'
                sh 'git branch -a'
                sh 'git status'

                // Build the Docker image
                sh "docker build -t rajeshtalla0209/votingapp-vote:${VERSION} ."
            }
        }

        stage('Run') {
            steps {
                // Run the Docker container and expose port 80
                sh "docker run -p 80:80 -d rajeshtalla0209/votingapp-vote:${VERSION}"
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Tag the image with your Docker Hub username and repository name
                    sh "docker tag rajeshtalla0209/votingapp-vote:${VERSION} rajeshtalla0209/votingapp-vote:${VERSION}"
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        // Push the image to Docker Hub
                        sh "docker push rajeshtalla0209/votingapp-vote:${VERSION}"
                    }
                }
            }
        }
    }
}
// final success one