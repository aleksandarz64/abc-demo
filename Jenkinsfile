pipeline {
   agent any

   environment {
       //GIT_URL = 'https://github.com/aleksandarz64/abc-demo.git'
       APP_NAME = 'abc-demo'
       // DOCKER_USERNAME = '99118822'
   }

   options {
    disableConcurrentBuilds()
    retry(1)
    skipStagesAfterUnstable()
    timeout(time: 10, unit: 'MINUTES')
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '1'))
   }

   stages {
      stage ('Build Docker image') {
          steps {
              echo "Building Docker image"
          }
      }

      stage ('Login to Docker HUB') {
          steps {
              echo "Login to Docker Hub"
              }
          }
      stage ('Notify') {
         steps {
              slackSend(channel:'update', message: "Job is successful, here is the info -  Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
         }
      }
   } // end of stages
}
//   post {
//     always {
//       echo "Build stage complete"
//     }
//   failure
//       echo "Build failed"
       //mail body: 'build failed', subject: 'Build failed!', to: 'devops@company.com'
 //    }

 //    success {
 //      echo "Build success"
//mail body: 'build succeeded', subject: 'Build Succeeded', to: 'devops@company.com'
 //    }
   
//}
