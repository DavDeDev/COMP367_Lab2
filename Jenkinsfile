pipeline {
  agent any
  triggers { pollSCM 'H/5 * * * *' }
  tools {
    maven 'MAVEN3'
  }

  stages {

    stage('Check out') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        bat 'mvn clean package'
      }
    }
    stage('Add Code Coverage') {
      steps {
        bat 'mvn jacoco:report'
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'target/site/jacoco/', reportFiles: 'index.html', reportName: 'Code Coverage Report'])
      }
    }

//     stage('Docker Build') {
//       steps {
//         script {
//           docker.build("your-image-name")
//         }
//       }
//     }
//
//     stage('Docker Login') {
//       steps {
//         withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
//           bat 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
//         }
//       }
//     }
//
//     stage('Docker Push') {
//       steps {
//         script {
//           docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-creds') {
//             docker.image("your-image-name").push("latest")
//           }
//         }
//       }
//     }
  }
}
