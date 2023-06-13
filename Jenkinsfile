pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // Checkout the source code from the repository
                git 'https://github.com/Navaneethakrishnan88/application-deployment.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build the Docker image
                sh 'docker build -t myapp:v1 .'
            }
        }
        
        stage('Deploy') {
            steps {
                // Stop and remove any existing container with the same name
                sh 'docker stop myapp_container || true'
                sh 'docker rm myapp_container || true'
                
                // Run the Docker container
                sh 'docker run -d -p 80:5000 --name myapp_container myapp:v1'
            }
        }
    }
}