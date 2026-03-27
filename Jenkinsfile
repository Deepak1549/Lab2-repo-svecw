pipeline {
    agent any

    stages {

        stage('Validate HTML') {
            steps {
                sh 'if [ -f registration.html ]; then echo "File found. Validation passed."; else echo "ERROR: Not found!"; exit 1; fi'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sh 'sudo cp registration.html /var/www/html/registration.html'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -s -o /dev/null -w "%{http_code}" http://localhost/registration.html'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed! Registration page is live.'
        }
        failure {
            echo 'Pipeline failed. Check the logs above.'
        }
    }
}
