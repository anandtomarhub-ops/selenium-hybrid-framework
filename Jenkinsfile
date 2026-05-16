pipeline {
    agent any

    tools {
        maven 'Maven 3.8'
        jdk 'JDK 11'
    }

    environment {
        REPORT_PATH = 'reports/ExtentReport.html'
    }

    stages {
        stage('Checkout') {
            steps {
                echo '========== Checking out source code =========='
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '========== Building the project =========='
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Run Regression Tests') {
            steps {
                echo '========== Running Regression Test Suite =========='
                sh 'mvn test -Dcucumber.filter.tags="@Regression"'
            }
            post {
                always {
                    echo '========== Tests Completed =========='
                }
            }
        }

        stage('Publish Reports') {
            steps {
                echo '========== Publishing Test Reports =========='
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'reports',
                    reportFiles: 'ExtentReport.html',
                    reportName: 'Extent Test Report'
                ])
            }
        }
    }

    post {
        success {
            echo '✅ Build and Tests PASSED!'
        }
        failure {
            echo '❌ Build or Tests FAILED! Check the report.'
        }
        always {
            cleanWs()
        }
    }
}
