pipeline {
   agent any

   environment
   {NEW_VERSION=1.0}

   stages {
     
       stage('Preparation') {
         steps {
               
             bat 'echo "Preparing"'
                     echo  "${env.BRANCH_NAME}"
                     echo "Running Releas version $ $NEW_VERSION with ${env.BUILD_ID} on ${env.JENKINS_URL}"
           
         }
          }
       stage('Build') {
         steps {
             bat 'echo "build"'
              }
          }
      }
      }
