pipeline {
  agent any
  triggers {
    pollSCM 'H/5 * * * *'
  }
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
      }
    }
    stage('Publish JaCoCo Report') {
      steps {
        jacoco(
          execPattern: '**/target/jacoco.exec',
          classPattern: '**/classes',
          sourcePattern: '**/src/main/java'
        )
      }
    }

    stage('Docker Build') {
      steps {
        script {
          docker.build("assignment3-image")
        }
      }
    }
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
