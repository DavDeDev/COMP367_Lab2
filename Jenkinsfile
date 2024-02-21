pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use Maven from global tool configuration
                tool 'Maven'
                bat """
                    C:/Users/pietr/OneDrive/Desktop/apache-maven-3.9.6/bin/mvn.cmd --v
                """
            }
        }
    }
}
