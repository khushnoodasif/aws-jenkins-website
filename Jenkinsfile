pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh "python unit_test.py"
            }
        }
        stage('Deploy to s3') {
            steps {
                echo 'Deploying..'
                sh "aws configure set region $AWS_REGION"
                sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"
                sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
                sh "aws s3 cp ./index.html s3://aws-jenkins-bucket"
                sh "aws s3 cp ./error.html s3://aws-jenkins-bucket"
                
            }
        }
    }
    post {
        success {
            echo 'success'
        }
        failure {
            echo 'failure'
        }
    }
}