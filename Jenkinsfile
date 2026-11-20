pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code source récupéré depuis GitHub'
            }
        }

        stage('Build calc-service') {
            steps {
                dir('calc-service') {
                    sh 'docker build -t 192.168.10.67:5000/calculator-calc:latest .'
                }
            }
        }

        stage('Build sum-service') {
            steps {
                dir('sum-service') {
                    sh 'docker build -t 192.168.10.67:5000/calculator-sum:latest .'
                }
            }
        }

        stage('Build sub-service') {
            steps {
                dir('sub-service') {
                    sh 'docker build -t 192.168.10.67:5000/calculator-sub:latest .'
                }
            }
        }

        stage('Build mul-service') {
            steps {
                dir('mul-service') {
                    sh 'docker build -t 192.168.10.67:5000/calculator-mul:latest .'
                }
            }
        }

        stage('Build div-service') {
            steps {
                dir('div-service') {
                    sh 'docker build -t 192.168.10.67:5000/calculator-div:latest .'
                }
            }
        }

        stage('Push images'){
            steps {
                sh 'docker push 192.168.10.67:5000/calculator-sub:latest'
                sh 'docker push 192.168.10.67:5000/calculator-calc:latest'
                sh 'docker push 192.168.10.67:5000/calculator-add:latest'
                sh 'docker push 192.168.10.67:5000/calculator-mul:latest'
                sh 'docker push 192.168.10.67:5000/calculator-div:latest'
            }
        }
    }

    post {
        success {
            echo 'CI : toutes les images ont été construites avec succès !'
        }
        failure {
            echo 'CI : échec du pipeline.'
        }
    }
}

