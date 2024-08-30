pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "fetch the source code from the directory path: "
                echo "compile this code and generate any necessary artifacts using Apache Maven, a comprehensive build management tool"
                echo "Maven will take the code and required dependencies to build the product"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Unit tests performed by JUnit which takes minor functional parts of the software to be tested individually to ensure the smooth running of the unit. Unit testing is a program testing method used to ascertain individual software components functionality, accuracy, and efficiency.'
                echo 'Integration tests performed by Protractor which tests the interactions between various components of an application and ensure that they work seamlessly together'
            }
            post{
                success{
                    emailext (
                        to: 'solanomigs@gmail.com',
                        subject: 'Tests status email!',
                        body: 'Testing success!',
                        attachLog: true
                    )
                    emailext attachLog: true, body: '', subject: ''
                }
            }            
        }
        stage('Code Analysis') {
            steps {
                echo 'Undergo Code Analysis with Akido Security which analzes source code for potential coding errors without running it. Used to identify and fix issues like bugs or security risks.'
            }
            }
        stage ('Security Scan') {
            steps {
                echo "Use Synk to identify and fix known vulnerabilities in dependencies as well as containers"
            }
            post{
                success{
                    emailext (
                        to: 'solanomigs@gmail.com',
                        subject: 'Security scan status email!',
                        body: 'Job security scan success!',
                        attachmentsPattern: '**/build.log'
                    )
                }
            }            
        }
        stage ('Deploy to Staging') {
            steps {
                echo "Deployment is handled by jenkins in this case to an AWS EC2 STAGING instance which is a cloud computing server which will handle CPU, memory, storage, and networking capacity for the product."
                sleep(time:10,unit:"SECONDS")
            }
        }
        stage ('Inegration tests on Staging') {
            steps {
                echo "Again, use JUnit to undergo integration tests which validates the interactions between the product's components and the staging environment to ensure everything works perfectly."
            }
        }
        stage ('Deploy to Production'){
            steps {
                echo "Deploy code to AWS EC2 production instance, our final destination for the product in which an Amazon Web Server EC2 instance will be used to host and operate the product making use of its CPU, memory, storage and networking capacity."
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
