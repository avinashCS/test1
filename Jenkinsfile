def gv
//
def user
node {
  wrap([$class: 'BuildUser']) {
    user = env.BUILD_USER_ID
  }
  
  emailext mimeType: 'text/html',
                 subject: "[Jenkins]${currentBuild.fullDisplayName}",
                 to: "sahu.avinash@gmail.com","acs_in@yahoo.com",
                 body: '''<a href="${BUILD_URL}input">click to approve</a>'''
}
//
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
     //
      stage('deploy') {
            input {
                message "Should we continue?"
                ok "Yes"
            }
            when {
                expression { user == 'sahu.avinash@gmail.com'}
            }
            steps {
                sh "echo 'describe your deployment' "
            }
        }
      //
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
