pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git 'https://github.com/Rushi5078/index-html-project.git'
            }
        }

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
