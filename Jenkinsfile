pipeline {
    agent { label 'docker-agent' }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Jaouaher999/landing-page-example'
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