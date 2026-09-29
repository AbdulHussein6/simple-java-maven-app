pipeline {
    agent any

    tools {
        // Use the Maven tool configured in Jenkins
        maven 'Maven'
    }

    options {
        skipStagesAfterUnstable()
    }

    stages {
        stage('Build') {
            steps {
                // Compile and package, skipping tests for now
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }

        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
            post {
                // Always archive test results, even if the tests fail
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }