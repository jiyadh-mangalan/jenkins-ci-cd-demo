// Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any // or agent { docker 'node:latest' } if you want to use a Docker agent

    environment {
        // Optional: Define environment variables
        NODE_ENV = 'development'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from SCM...'
                git 'https://github.com/jiyadh-mangalan/jenkins-ci-cd-demo.git' // Replace with your repo URL
            }
        }

        stage('Build') {
            steps {
                echo 'Installing Node.js dependencies...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test' // This will execute the "test" script in package.json
            }
        }

        stage('Deploy (Simulated)') {
            steps {
                echo 'Simulating deployment to a target environment...'
                // In a real scenario, this would involve:
                // - Copying artifacts to a server (scp, rsync)
                // - Running deployment scripts (Ansible, Terraform)
                // - Deploying to a cloud service (AWS, Azure, GCP)
                // - Deploying Docker images to Kubernetes
                sh 'echo "Application deployed to http://your-simulated-server:3000"'
                // You could even run the app briefly in a Docker container here
                // sh 'docker build -t my-app .'
                // sh 'docker run -d -p 9091:3000 my-app'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
            // mail to: 'jiyadhkali@gmail.com', subject: 'Jenkins Build Success!', body: 'Your application build and deployment succeeded.'
        }
        failure {
            echo 'Pipeline failed!'
            // mail to: 'jiyadhkali@gmail.com', subject: 'Jenkins Build FAILED!', body: 'Your application build or deployment failed. Check logs.'
        }
    }
}
