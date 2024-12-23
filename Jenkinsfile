pipeline {
    agent any
    environment {
        AWS_REGION = 'us-east-1' // Set your AWS region
        S3_BUCKET = 'your-s3-bucket-name' // Replace with your S3 bucket name
        FILE_PATH = 'path/to/your/file.txt' // Replace with the path to the file you want to upload
    }
    stages {
        stage('Prepare') {
            steps {
                echo 'Preparing the environment...'
                // Ensure AWS CLI is installed and configured
                sh 'aws --version'
            }
        }
        stage('Upload File to S3') {
            steps {
                echo 'Uploading file to S3 bucket...'
                sh '''
                aws s3 cp ${FILE_PATH} s3://${S3_BUCKET}/
                '''
            }
        }
    }
    post {
        success {
            echo 'File uploaded successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
