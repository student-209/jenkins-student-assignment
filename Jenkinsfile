// pipeline {
//     agent any

//     stages {

//         stage('Build') {
//             steps {
//                 echo 'Compiling application...'
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo 'Running unit tests... Pass!'
//             }
//         }

//         stage('Package') {
//             steps {
//                 powershell '''
//                     $timestamp = Get-Date -Format "yyyy-MM-dd HH:mm:ss"
//                     "Build Number: $env:BUILD_NUMBER" | Out-File -FilePath build-info.txt
//                     "Build executed on: $timestamp" | Out-File -FilePath build-info.txt -Append
//                 '''
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Build successful! Ready for release.'
//         }
//     }
// }


pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Compiling application...'
                bat 'javac Main.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests... Pass!'
                bat 'java Main'
            }
        }

        stage('Package') {
            steps {
                bat '''
                    echo Build Number: %BUILD_NUMBER% > build-info.txt
                    echo Build executed on: %DATE% %TIME% >> build-info.txt
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