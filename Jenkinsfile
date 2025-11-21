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
        stage('Upload Artifact to S3') {
            steps {
                sh '''
                    WAR_FILE=/opt/homebrew/opt/tomcat/libexec/webapps/my-app.war
                    BUCKET=harsh-s3-maven-bucket1q2w3e4r
                    VERSION=$(date +%Y-%m-%d-%H-%M-%S)

                    
                    echo "Uploading $WAR_FILE to S3 bucket $BUCKET"
                    aws s3 cp $WAR_FILE s3://$BUCKET/GRADLE-artifacts/my-app.war
                '''
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
