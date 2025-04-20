pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t nodejs-demo-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests inside the container...'
                sh 'docker run --rm nodejs-demo-app npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying app...'
                sh 'docker rm -f nodejs-demo-app || true'
                sh 'docker run -d -p 3000:3000 --name nodejs-demo-app nodejs-demo-app'
            }
        }
    }
}
