pipeline {
    agent any

    stages {

        // stage('Checkout') {
        //     steps {
        //         checkout scm
        //     }
        // }

        stage('Gradle Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        // stage('Test') {
        //     steps {
        //         sh './gradlew test'
        //     }
        // }

    }

    post {
        success {
            echo "Build completed successfully!"
        }
        failure {
            echo "Build failed!"
        }
    }
}
