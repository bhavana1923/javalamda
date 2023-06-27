pipeline {
    agent any

    environment {
        function_name = 'java'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build'
                sh 'mvn package'
            }
        }

        stage('Push') {
            steps {
                echo 'Push'

                sh "aws s3 cp target/sample-1.0.3.jar s3://java12ps"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Build'

                sh "aws lambda update-function-code --function-name $function_name --s3-bucket  java12ps-s3-key sample-1.0.3.jar"
            }
        }
    }
}
