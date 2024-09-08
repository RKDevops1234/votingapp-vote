pipeline {
    agent any
    
     script {
     // Define a variable for the version
    def version = '1'
     }
     
    stages {
        stage('Build') {
            steps {
                // Checkout the code
                git 'https://github.com/RKDevops1234/votingapp-vote.git'

                // Build the Docker image
                sh 'docker build -t rajeshtalla0209/votingapp-vote:${version}  .'
            }
        }

        stage('Run') {
            steps {
                // Run the Docker container and expose port 80
                sh 'docker run -p 80:80 -it rajeshtalla0209/votingapp-vote:${version}'
            }
        }
    }
        stage('Push to Docker Hub') {
            steps {
                
                // Tag the image with your Docker Hub username and repository name
                sh 'docker tag your-image-name rajeshtalla0209/votingapp-vote:${version}'
                docker.withRegistry( 'https://registry.hub.docker.com', 'docker' ) {
                // Push the image to Docker Hub
                sh 'docker push rajeshtalla0209/votingapp-vote:${version}'
            }
        }
    }
}
