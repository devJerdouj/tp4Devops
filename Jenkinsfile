pipeline {
    environment {
        registry = "hjerdouj/tp4"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any

    stages {
        stage('Cloning Git') {
            steps {
                git 'https://github.com/devJerdouj/tp4Devops'
            }
        }

        stage('Building image') {
            steps {
                script {
                    dockerImage = docker.build("${registry}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Test image') {
            steps {
                script {
                    // Exécution de vos tests (ici, simple message d’exemple)
                    echo "Tests passed"
                }
            }
        }

        stage('Publish Image') {
            steps {
                script {
                    // Se connecte à Docker Hub, puis pousse l’image construite
                    docker.withRegistry('', registryCredential) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
