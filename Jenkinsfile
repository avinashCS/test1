pipeline {
   agent any

  

   stages {
     
       stage('Preparation') {
         steps {
               
             bat 'echo "Preparing"'
                     echo  "${env.BRANCH_NAME}"
                     echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
           
         }
          }
       stage('Build') {
         steps {
             bat 'echo "build"'
              }
          }
      }
      }
