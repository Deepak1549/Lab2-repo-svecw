pipeline {
    agent any

    stages {

        stage('Validate HTML') {
            steps {
                sh '''
                    echo "Checking if registration.html exists..."
                    if [ -f registration.html ]; then
                        echo "File found. Validation passed."
                    else
                        echo "ERROR: registration.html not found!"
                        exit 1
                    fi
                '''
            }
        }

        stage('Deploy to Web Server') {
            steps {
                sh '''
                    sudo cp registration.html /var/www/html/registration.html
                    echo "Deployment successful!"
                '''
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
```

**3. Scroll down → Click "Commit changes"**
- Select **"Commit directly to the master branch"**
- Click **Commit changes**

---

### Verify the Commit Was Saved

After committing, go to:
```
https://github.com/Deepak1549/Lab2-repo-svecw/commits/master
