pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo '01 Hello Bunkakai'
            }
        }
        stage('Build') {
            steps {
                echo '02 Build'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'AwsTest',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/Pipeline/index.html s3://bunkakai-deploy/')
                }
            }
        }
        stage('Test') {
            steps {
                echo '04 Test'
            }
        }
        stage('Release') {
            steps {
                echo '05 Release'
            }
        }
    }
}
