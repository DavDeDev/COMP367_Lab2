pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use Maven from global tool configuration
                tool 'Maven'
                bat """
                    export M2_HOME=C:\Users\pietr\OneDrive\Desktop\apache-maven-3.9.6
                    export PATH=$PATH:$M2_HOME/bin
                    mvn --version
                """
            }
        }
    }
}
