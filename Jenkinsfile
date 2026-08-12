pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Compiling application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests... Pass!'
            }
        }

        stage('Package') {
            steps {
                powershell '''
                    $timestamp = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
                    "Build Number: $env:BUILD_NUMBER" | Out-File -FilePath build-info.txt
                    "Build executed on: $timestamp" | Out-File -FilePath build-info.txt -Append
                '''
            }
        }
    }

    post {
        success {
            echo 'Build successful! Ready for release.'
        }
    }
}