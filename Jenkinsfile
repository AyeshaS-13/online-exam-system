pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/AyeshaS-13/online-exam-system.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t online-exam-system:1.0 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop online-exam-container || exit 0'
                bat 'docker rm online-exam-container || exit 0'
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d --name online-exam-container -p 8081:5000 online-exam-system:1.0'
            }
        }

        stage('Deployment Verification') {
            steps {
                echo 'Online Examination System deployed successfully.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD PIPELINE COMPLETED SUCCESSFULLY'
        }

        failure {
            echo 'CI/CD PIPELINE FAILED'
        }
    }
}
