pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/fredericEducentre/landing-page-example.git'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'alwaysdata-pass', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh '''
                        sshpass -p "$PASS" scp -o StrictHostKeyChecking=no index.html $USER@ssh-jaouaher.alwaysdata.net:/home/jaouaher/www/
                    '''
                }
            }
        }
    }
}