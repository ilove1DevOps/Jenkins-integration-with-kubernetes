pipeline {
    agent any    
    stages {
        stage('Build') {
            steps {
                sh "docker build -t your-image:e${BUILD_NUMBER} ."
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'Docker_Hub_piyushdhir121', variable: 'DockerHub_cred')]) {
                    sh "docker login -u piyushdhir121 -p '${DockerHub_cred}'"
                    echo 'Login Completed'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh "docker tag your-image:e${BUILD_NUMBER} piyushdhir121/your-image:e${BUILD_NUMBER}"
                sh "docker push piyushdhir121/your-image:e${BUILD_NUMBER}"
                echo "Pushed to Docker Hub. Check Docker Hub for the image with tag e${BUILD_NUMBER}."
            }
        }
    }
}
