pipeline {
    agent any
    tools {
        // Use the Maven tool configured in Jenkins
        maven 'Maven'
    }
    stages {
        stage('Build') {
            steps {
                // Compile and package, skipping tests for now
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}