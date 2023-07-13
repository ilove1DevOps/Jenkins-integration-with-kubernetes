{
agent any    
stages {
    stage('Build') {
        steps {
            sh 'docker build -t your-image:e1 .'
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
            sh 'docker tag your-image:e1 piyushdhir121/your-image:e1'
            sh 'docker push piyushdhir121/your-image:e1'
            echo 'Pushed to Docker Hub. Check Docker Hub for the image.'
        }
    }
}
