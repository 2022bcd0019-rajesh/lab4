pipeline {
    agent any

    environment {
        PATH = "/var/jenkins_home/.local/bin:${env.PATH}"
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install --break-system-packages -r requirements.txt'
            }
        }

        stage('Train Model') {
            steps {
                sh 'python3 scripts/train.py'
            }
        }

        stage('Print Metrics') {
            steps {
                echo "Name: V. Raajeshwar Reddy"
                echo "Roll No: 2022BCD0019"
                sh 'python3 scripts/evaluate.py || echo "evaluate.py not present — skipping"'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t rajeshwar250/wine_predict_2022bcd0019:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                        echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                        docker push rajeshwar250/wine_predict_2022bcd0019:latest
                    '''
                }
            }
        }
    }
}

