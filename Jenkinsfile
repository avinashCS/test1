pipeline {
   agent any

   environment
   {
      NEW_VERSION=1.0
      server_cred=credentials('GitHub')
   }
 parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

   stages {
     
       stage('Preparation') {
         steps {
               
             bat 'echo "Preparing"'
                     echo  "${env.BRANCH_NAME}"
            echo " ${env.JAVA_HOME}"
                     echo "Running Release version $NEW_VERSION with ${env.BUILD_ID} on ${env.JENKINS_URL}"
                     echo "$server_cred"
                     bat '$server_cred'
         }
          }
       stage('Build') {
         steps {
             bat 'echo "build"'
              }
          }
      stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
               echo "TEST.......ing"
            }
        }

      stage("Deploy") {
           steps {
             bat 'echo "Deploy"'
              }
          }
            
      
      }
      }
