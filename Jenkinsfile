pipeline {
    agent any

    environment {
        FRONTEND_SERVER = "ec2-user@184.72.201.212"
        FRONTEND_PATH   = "/var/www/html"
        GIT_REPO        = "https://github.com/Rushi5078/index-html-project.git"
        SSH_KEY         = "/var/lib/jenkins/.ssh/my-key.pem"  // Jenkins private key
        WORKSPACE_PATH  = "${env.WORKSPACE}"                 // Jenkins workspace
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
                    # Step 1: Copy files to ec2-user home folder
                    scp -i ${SSH_KEY} ${WORKSPACE_PATH}/index.html ${WORKSPACE_PATH}/styles.css ${FRONTEND_SERVER}:~/

                    # Step 2: Move files to /var/www/html using sudo on frontend
                    ssh -i ${SSH_KEY} ${FRONTEND_SERVER} "sudo mv ~/index.html ${FRONTEND_PATH}/ && sudo mv ~/styles.css ${FRONTEND_PATH}/"
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
