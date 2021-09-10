def gv
pipeline {
   agent any

   environment
   {
      temp_NEW_VERSION=1.0
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
                     echo "Running temp Release version $temp_NEW_VERSION with ${env.BUILD_ID} on ${env.JENKINS_URL}"
                  
            script {
                   gv = load "script.groovy" 
                }

                 
         }
          }
       stage('Build') {
         steps {
             bat 'echo "build"'
            
            script{
            gv.buildApp()
            }
              }
          }
      stage("test") {
         input {
                message "Can we Proceed?"
                ok "Yes"
                submitter "Digital Varys"
                parameters {
                    string(name: 'PERSON', defaultValue: 'DigiralVarys', description: 'Member')
                }
         }
            
            
            when {
                expression {
                    params.executeTests
                }
            }
         
            steps {
               echo "${PERSON}, is proceeding..."
               echo "TEST.......ing"
                 script {
                    gv.testApp()
                }

            }
        }

      stage("Deploy") {
         
           steps {
              
             bat 'echo "Deploy"'
              echo "deploying version ${VERSION}"
              
               script {
                    gv.deployApp()
                }
              bat 'dir'

              }
          }
            
      
      }
      }
