```groovy
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building website...'
            }
        }

        stage('Test') {
            steps {
                bat '''
                    if not exist index.html exit /b 1
                    if not exist style.css exit /b 1
                    if not exist script.js exit /b 1
                '''

                echo 'Website files found. Test successful!'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    if not exist C:\\JenkinsDeploy\\my-web-project mkdir C:\\JenkinsDeploy\\my-web-project

                    copy /Y index.html C:\\JenkinsDeploy\\my-web-project\\index.html
                    copy /Y style.css C:\\JenkinsDeploy\\my-web-project\\style.css
                    copy /Y script.js C:\\JenkinsDeploy\\my-web-project\\script.js
                '''

                echo 'Website deployed successfully!'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
```
