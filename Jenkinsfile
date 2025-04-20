pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t nodejs-demo-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests inside the container...'
                bat 'docker run --rm nodejs-demo-app npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying app...'
                bat 'docker stop nodejs-demo-app || exit 0'
                bat 'docker rm nodejs-demo-app || exit 0'
                bat 'docker run -d -p 3000:3000 --name nodejs-demo-app nodejs-demo-app'
            }
        }
    }
}
