pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/your-username/index-html-project.git'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/index.html
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
