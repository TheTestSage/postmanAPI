pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building WAR file or project...'
                // Add actual build commands here if needed
            }
        }

        stage('Deploy to QA') {
            steps {
                echo 'Deploying to QA environment...'
                // Add deployment steps to QA
            }
        }

        stage('QA Verification') {
            steps {
                echo 'Running smoke/verification checks on QA...'
                // Add verification scripts if applicable
            }
        }

        stage('Deploy to Stage') {
            steps {
                echo 'Deploying to staging environment...'
                // Add staging deployment logic
            }
        }

        stage('Stage Verification') {
            steps {
                echo 'Verifying staging deployment...'
                // Add staging-level checks or integrations
            }
        }

        stage('Deploy to Prod') {
            steps {
                echo 'Deploying to production environment...'
                // Final prod deployment step
            }
        }

        stage('Checkout API Tests') {
            steps {
                git url: 'https://github.com/TheTestSage/postmanAPI'
            }
        }

        stage('Run API Test Cases') {
            steps {
                bat 'newman run Restful-Booker.postman_collection.json -e Booker_QA.postman_environment.json -r cli,html --reporter-html-export report\\report.html'
            }
        }

        stage('Publish HTML Report') {
            steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'report',
                    reportFiles: 'report.html',
                    reportName: 'Restful Booker API Report',
                    reportTitles: ''
                ])
            }
        }
    }
}
