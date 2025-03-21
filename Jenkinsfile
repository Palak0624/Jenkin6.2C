pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'This stage compiles and packages the application using a build automation tool like Maven or Gradle.'
                echo 'Building the application...'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    try {
                        echo 'Running unit and integration tests...'
                        
                        // Simulate test execution
                        sh 'echo "Running tests..."'

                        echo 'Tests passed successfully.'
                        
                        // Send email notification for test success
                        mail (subject: "Jenkins Pipeline: Tests Passed ✅",
                            body: """
                                <p>All unit and integration tests passed successfully.</p>
                                <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                            """,
                            to: 'palak4832.be23@chitkara.edu.in')
                    } catch (Exception e) {
                        echo 'Tests failed! Sending failure email...'
                        
                        // Send email notification for test failure
                        mail (subject: "Jenkins Pipeline: Tests Failed ❌",
                            body: """
                                <p>Unit and integration tests failed. Please check the logs.</p>
                                <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                            """,
                            to: 'palak4832.be23@chitkara.edu.in')
                        
                        error "Failing the build due to test failure."
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production environment...'
            }
        }
    }

    post {
        always {
            echo 'Sending final pipeline status notification...'
            
            mail (subject: "Jenkins Pipeline Execution Status 📩",
                body: """
                    <p>The pipeline has completed execution.</p>
                    <p>Final Status: ${currentBuild.currentResult}</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                """,
                to: 'palak4832.be23@chitkara.edu.in')
        }
    }
}
