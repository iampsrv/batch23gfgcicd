pipeline {
    agent any

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
                sh "docker build -t psrv3/myflaskapp"
                echo 'Docker image build successfully'
            }
        }    
        stage('Login to Dockerhub') {
            steps {
                echo 'Login successfully'
            }
        }
        stage('Push to Dockerhub') {
            steps {
                sh "docker push psrv3/myflaskapp"
                echo 'Docker image push successfully'
            }
        }  
    }
}
