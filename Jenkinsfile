pipeline {
    agent any
    environment {
        APP_NAME = "sample-app"
        GIT_REPO = "https://github.com/divyaparashuram0101-tech/new-repo.git"
    }
  
    stages {
        stage('Checkout Code') {
            steps {
                echo " Cloning source code from ${GIT_REPO}"
                git branch: 'main', url: "${GIT_REPO}"
            }
        }

stage('Build') {
            steps {
                echo " Building ${APP_NAME}..."
                sh '''
                    echo "Installing dependencies..."
                    sleep 2
                    echo "Build successful!"
                '''
            }
        }

  stage('Test') {
            steps {
                echo " Running tests..."
                sh '''
                    echo "Executing test cases..."
                    sleep 1
                    echo "All tests passed!"
                '''
            }
        }

  stage('Archive Artifacts') {
            steps {
                echo " Archiving build output..."
                sh 'mkdir -p build && echo "Build artifact for ${APP_NAME}" > build/output.txt'
                archiveArtifacts artifacts: 'build/**/*.txt', fingerprint: true
            }
        }

stage('Deploy') {
            steps {
                echo " Deploying application..."
                sh 'echo "Deployment completed successfully!"'
            }
        }
    }


    post {
        success {
            echo " Pipeline completed successfully!"
        }
        failure {
            echo " Pipeline failed — please check logs!"
        }
    }
}
