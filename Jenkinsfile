pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'souravhajra12345/my-py-app:latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/souravhajra123/ElevateLabsTask2.git'
            }
        }

        stage('Test Flask App') {
            steps {
                echo "Testing app.py"
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh "docker build -t $DOCKER_IMAGE ."
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DOCKER_HUB_CREDENTIALS', usernameVariable: 'DOCKER_HUB_USERNAME', passwordVariable: 'DOCKER_HUB_PASSWORD')]) {
                    sh "echo $DOCKER_HUB_PASSWORD | docker login -u $DOCKER_HUB_USERNAME --password-stdin"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push $DOCKER_IMAGE"
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "Stopping old container if running..."
                sh "docker rm -f my-py-container || true"

                echo "Running new container..."
                sh "docker run -d -p 5000:5000 --name my-py-container $DOCKER_IMAGE"
            }
        }
    }

    post {
        success {
            echo '🎉 Deployment successful!'
        }
        failure {
            echo '❌ Something went wrong.'
        }
    }
}

