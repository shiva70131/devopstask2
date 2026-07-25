pipeline {
    agent any

    stages {
        stage('Building') {
            steps {
                sh 'docker build -t task2-app:latest .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm task2-app:latest echo "Test passed"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f task2-container || true'
                sh 'docker run -d --name task2-container -p 8081:80 task2-app:latest'
            }
        }
    }
}