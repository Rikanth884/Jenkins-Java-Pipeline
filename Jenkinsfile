pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'BUILD STAGE STARTED'

                sh 'mkdir -p build'

                sh 'javac -d build src/Hello.java'

                sh 'jar --create --file build/Hello.jar -C build Hello.class'

                echo 'BUILD STAGE COMPLETED SUCCESSFULLY'
            }
        }

        stage('Test') {
            steps {
                echo 'TEST STAGE STARTED'

                sh 'java -cp build Hello'

                sh 'java -cp build Hello | grep -q "Hello World!"'

                echo 'TEST STAGE COMPLETED SUCCESSFULLY'
            }
        }

        stage('Deploy') {
            steps {
                echo 'DEPLOY STAGE STARTED'

                sh 'mkdir -p deploy'

                sh 'cp build/Hello.jar deploy/'

                echo 'APPLICATION DEPLOYED SUCCESSFULLY'
            }
        }
    }

    post {
        success {
            echo 'PIPELINE EXECUTED SUCCESSFULLY!'
        }

        failure {
            echo 'PIPELINE EXECUTION FAILED!'
        }
    }
}
