pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'checkout the code'
            }
        }
        stage('Setup the env') {
            steps {
                echo 'Setup the env'
            }
        }
        stage('Test') {
            steps {
                echo 'Test'
            }
        }
        stage('Build docker image') {
            steps {
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
                echo 'Docker image push successfully'
            }
        }  
    }
}
