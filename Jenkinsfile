pipeline {
   agent any

   environment
   {
      NEW_VERSION=1.0
      server_cred=credentials('GitHub')
   }

   stages {
     
       stage('Preparation') {
         steps {
               
             bat 'echo "Preparing"'
                     echo  "${env.BRANCH_NAME}"
            echo " ${env.JAVA_HOME}"
                     echo "Running Release version $NEW_VERSION with ${env.BUILD_ID} on ${env.JENKINS_URL}"
                     echo "$server_cred"
         }
          }
       stage('Build') {
         steps {
             bat 'echo "build"'
              }
          }
      }
      }
