pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Checkout the code
                git 'https://github.com/RKDevops1234/votingapp-vote.git'

                // Build the Docker image
                sh 'docker build -t rajeshtalla0209/votingapp-vote:1  .'
            }
        }

        stage('Run') {
            steps {
                // Run the Docker container and expose port 80
                sh 'docker run -p 80:80 -it rajeshtalla0209/votingapp-vote:1'
            }
        }
    }
}