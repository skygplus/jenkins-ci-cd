pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Starting build...'

                sh 'python3 --version'

                sh 'python3 -m venv .venv'

                sh '.venv/bin/python -m pip install --upgrade pip'

                sh '.venv/bin/python -m pip install -r requirements.txt'

                echo 'Build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'

                sh '.venv/bin/python -m pytest --junitxml=test-results.xml'
            }

            post {
                always {
                    junit 'test-results.xml'
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'

                sh 'rm -rf build'
                sh 'mkdir -p build'

                sh 'cp app.py build/'
                sh 'cp requirements.txt build/'

                archiveArtifacts artifacts: 'build/**',
                                 fingerprint: true

                echo 'Application packaged successfully.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'

                sh 'rm -rf deployment'
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