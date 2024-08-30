pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "fetch the source code from the directory path: "
                echo 'compile this code and generate any necessary artifacts'
            }
        }
        stage('Test') {
            steps {
                echo 'unit tests'
                echo 'integration tests'
            }
        }
        stage('Code') {
            steps {
                echo 'check the quality of the code'
            }
            }
        stage ('Deploy') {
            steps {
                echo "deploy the application to a testing environment: "
            }
        }
        stage ('Approval') {
            steps {
                sleep(time:10,unit:"SECONDS")
            }
        }
        stage ('Polling SCM Test stage') {
            steps {
                sleep(time:10,unit:"SECONDS")
            }
        }        
        stage ('Deploy to Production'){
            steps {
                echo "Deploy code to AWS!"
            }
            post{
                success{
                    mail to: "solanomigs@gmail.com",
                    subject: "Build status email",
                    body: "Build was successful!"
                }
            }
        }
    }
}
