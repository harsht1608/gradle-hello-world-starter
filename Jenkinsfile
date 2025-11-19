pipeline {
    agent any

    tools {
        // Make sure Gradle is installed and configured in Jenkins → Global Tool Configuration
        gradle "gradle-latest"
    }

    stages {

        // stage('Checkout') {
        //     steps {
        //         checkout scm
        //     }
        // }

        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }

    }

    post {
        always {
            junit 'build/test-results/test/*.xml'
        }
    }
}
