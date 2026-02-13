pipeline {
    agent any

    stages {

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
                echo "Name: V. Raajeshwar Reddy"
                echo "Roll No: 2022BCD0019"
                sh 'python evaluate.py'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t rajeshwar250/wine_predict_2022bcd0019:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push rajeshwar250/wine_predict_2022bcd0019:latest'
            }
        }
    }
}
