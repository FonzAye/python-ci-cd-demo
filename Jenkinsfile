pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'python-ci-cd-demo-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/FonzAye/python-ci-cd-demo.git'
            }
        }

        stage('Validate') {
            steps {
                script {
                    sh 'ls -la'
                }
            }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    sh 'docker run $DOCKER_IMAGE'
                }
            }
        }

        stage('Deploy Application') {
            steps {
                script {
                    sh 'docker run -d -p 5000:5000 --name python-app $DOCKER_IMAGE'
                }
            }
        }
    }
}
