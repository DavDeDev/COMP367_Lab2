pipeline {
  agent any
  tools {
    maven 'MAVEN3'
  }
  environment {
    DOCKERHUB_PWD = credentials('DOCKERHUB_PWD')
  }

  stages {

    stage('Check out') {
      steps {
        git url: 'https://github.com/DavDeDev/COMP367_Lab2.git', branch: 'main'
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
        //       Scripted way
        //         script {
        //           docker.build("davidp02/david_lab03:${BUILD_NUMBER}")
        //         }
        //         Declarative way
        bat "docker build -t davidp02/david_lab03:${BUILD_NUMBER} ."
      }
    }
//     stage('Docker Login') {
//         steps {
//           bat "docker login -u davidp02 -p ${DOCKERHUB_PWD}"
//         }
//   }
}
}
