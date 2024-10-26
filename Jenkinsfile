pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/Ram495-ctrl/CI-CD-Pipeline-jenkins-github-actions.git'  
        ECR_REPO = '975050024946.dkr.ecr.us-west-2.amazonaws.com/lucky-repos'
        DOCKER_IMAGE_TAG = "${ECR_REPO}:${BUILD_ID}"
        AWS_REGION = 'us-west-2'
        K8S_MANIFEST_PATH = 'k8s/'  
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: "${REPO_URL}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE_TAG)
                }
            }
        }

        stage('Login to ECR') {
            steps {
                script {
                    sh """
                    aws ecr get-login-password --region ${AWS_REGION} | docker login --username AWS --password-stdin ${ECR_REPO}
                    """
                }
            }
        }

        stage('Push Docker Image to ECR') {
            steps {
                script {
                    docker.withRegistry("${ECR_REPO}") {
                        sh "docker push ${DOCKER_IMAGE_TAG}"
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh """
                    kubectl set image -f ${K8S_MANIFEST_PATH}/deployment.yaml python-container=${DOCKER_IMAGE_TAG} --record
                    kubectl apply -f ${K8S_MANIFEST_PATH}
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
