pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Starting build...'

                sh 'python3 --version'

                sh 'python3 -m pip install --upgrade pip'

                sh 'pip3 install -r requirements.txt'

                echo 'Build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'

                sh 'pytest'

                echo 'All tests passed.'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'

                sh 'mkdir -p build'

                sh 'cp app.py build/'

                sh 'cp requirements.txt build/'

                echo 'Application packaged successfully.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'

                sh 'mkdir -p deployment'

                sh 'cp build/app.py deployment/'

                echo 'Deployment simulation completed.'
            }
        }
    }

    post {

        success {
            echo 'CI/CD PIPELINE COMPLETED SUCCESSFULLY!'
        }

        failure {
            echo 'CI/CD PIPELINE FAILED. Check the console output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}