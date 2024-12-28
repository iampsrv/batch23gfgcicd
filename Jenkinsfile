pipeline {
    agent any
    environment {
        IMAGE_NAME = 'psrv3/devopsbatch29'
        IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
    }   

    stages {
        stage('Checkout') {
            steps {
                git "https://github.com/iampsrv/batch29gfgcicd.git"
                echo 'checkout the code'
            }
        }
        stage('Setup the env') {
            steps {
                sh "pip install flask --break-system-packages"
                echo 'Setup the env'
            }
        }
        stage('Test') {
            steps {
                sh "pytest"
                echo 'Test'
            }
        }
        stage('Build docker image') {
            steps {
                sh "docker build -t ${IMAGE_TAG} ."
                echo 'Docker image build successfully'
            }
        }    
        stage('Login to Dockerhub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
                sh 'docker login -u psrv3 -p ${dockerhubpwd}'}
                echo 'Login successfully'
            }
        }
        stage('Push to Dockerhub') {
            steps {
                sh "docker push ${IMAGE_TAG}"
                echo 'Docker image push successfully'
            }
        }
        stage('Deploy latest docker image') {
            steps {
                sh "docker run -it -p 5000:5000 ${IMAGE_TAG}"
                echo 'Docker image ran successfully'
            }
        }    
    }
}
