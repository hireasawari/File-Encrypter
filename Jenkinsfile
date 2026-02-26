pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                echo "Building Java project..."
                ls
                cd "Password Protection"
                mkdir -p build
                javac -d build src/*.java
                echo "Build successful"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Packaging File-Encrypter Application..."
                cd "Password Protection"
                jar cf FileEncrypter.jar -C build .
                echo "Deployment successful - Artifact ready"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
