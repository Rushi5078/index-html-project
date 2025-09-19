pipeline {
    agent any

    environment {
        FRONTEND_SERVER = "ec2-user@184.72.201.212"  // Your frontend server
        FRONTEND_PATH   = "/var/www/html"           // Apache default directory
        GIT_REPO        = "https://github.com/Rushi5078/index-html-project.git"
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning GitHub repository..."
                git branch: 'main', url: "${GIT_REPO}"
            }
        }

        stage('Deploy to Frontend Server') {
            steps {
                echo "Deploying files to frontend server..."
                sh """
                    scp index.html styles.css ${FRONTEND_SERVER}:${FRONTEND_PATH}/
                """
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
