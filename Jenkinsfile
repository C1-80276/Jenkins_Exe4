pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80276/Jenkins_Exe4.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    sh 'echo dckr_pat_PaLl5Fxzkq8et76Hg8CaWv9__SQ | docker login -u chiraag77 --password-stdin'
                    sh 'docker build -t chiraag77/madara_speech .'
                    sh 'docker image push chiraag77/madara_speech'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'minikube kubectl -- apply -f rs+service.yaml'
                }
            }
        }
    }
}

