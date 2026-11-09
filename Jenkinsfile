pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Source code checked out from GitHub.'
            }
        }

        stage('Build') {
            steps {
                script {
                    if (!fileExists('index.html')) {
                        error 'Build failed: index.html was not found.'
                    }
                    if (!fileExists('css/style.css')) {
                        error 'Build failed: css/style.css was not found.'
                    }
                }
                echo 'Build check passed.'
            }
        }

        stage('Test') {
            steps {
                script {
                    def html = readFile('index.html')
                    if (!html.contains('Welcome to Continuous Integration!')) {
                        error 'Test failed: expected heading was not found.'
                    }
                    if (!html.contains('css/style.css')) {
                        error 'Test failed: stylesheet is not linked.'
                    }
                }
                echo 'Basic website tests passed.'
            }
        }

        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'index.html,css/**',
                                 fingerprint: true
                echo 'Deployment package archived in Jenkins.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check Console Output for details.'
        }
    }
}
