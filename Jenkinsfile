pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Train Model') {
            steps {
                sh 'python train.py'
            }
        }

        stage('Print Metrics') {
            steps {
                echo "Name: Rajeshwar Reddy"
                echo "Roll No: 2022BCD0019"
                sh 'python evaluate.py'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t YOUR_DOCKERHUB_USERNAME/model:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push YOUR_DOCKERHUB_USERNAME/model:latest'
            }
        }
    }
}
