pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/python-jenkins-docker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-python-app:${env.BUILD_ID}")
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    docker.image("my-python-app:${env.BUILD_ID}").inside {
                        sh 'python -m unittest discover || true'
                    }
                }
            }
        }
    }
}
