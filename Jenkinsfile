pipeline {
    agent any
    stage('Test') {
                steps {
                   echo 'This is a test for pipeline
                   !'
                }
            }

    stages {
        stage('Build') {
            steps {
                script {
                    bat 'mvn clean install'
                }
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
    }
}
