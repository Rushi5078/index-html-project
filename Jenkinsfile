pipeline {
    agent any

    stages {
        stage('Deploy to NGINX') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/
                sudo cp styles.css /var/www/html/
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
