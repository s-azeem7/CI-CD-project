pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/<your-username>/jenkins-ci-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-ci-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run --name myjenkinsapp -d jenkins-ci-app'
            }
        }
        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
            }
        }
    }
    post {
        always {
            sh 'docker stop myjenkinsapp || true'
            sh 'docker rm myjenkinsapp || true'
        }
    }
}
