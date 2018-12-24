pipeline {
    agent any
    parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
    stages {
        stage('Branch Selector')
        {
            steps{
             git branch: "${params.BRANCH}", url: 'https://github.com/mkuma283/Test2.git'
            }
        }
        stage('clone repo, build, clean workspace, copy files from 1 loc 2 another') { 
            steps {
                bat 'C:\\Windows\\Microsoft.NET\\Framework\\v3.5\\MSBuild.exe "TestProject.sln"'
                cleanWs()
                //Change the local folder path as per requirement.
               // bat "rmdir C:\\Users\\mkuma283\\Desktop\\test /s /q"
              // bat "mkdir C:\\Users\\mkuma283\\Desktop\\test"
              //  bat("xcopy C:\\Users\\mkuma283\\Test2 C:\\Users\\mkuma283\\Desktop\\test /S /Q /Y /O /X /E /H /K")
       }
        }
    }
     post {
      always {
          script {
              if (currentBuild.result == null) {
                  currentBuild.result = 'SUCCESS'    
              }
          }    
          step([$class: 'Mailer',
            notifyEveryUnstableBuild: true,
            recipients: "manisha_kumari28@optum.com",
            sendToIndividuals: true])
            
      }
  }
   
}

