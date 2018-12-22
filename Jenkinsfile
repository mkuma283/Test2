pipeline {
    agent any 
    stages {
        stage('clone repo and clean') { 
            steps {
                deleteDir()
                bat "git clone https://github.com/mkuma283/Test2.git"
                bat 'C:\\Windows\\Microsoft.NET\\Framework\\v3.5\\MSBuild.exe "C:\\Program Files (x86)\\Jenkins\\workspace\\Test\\Test2\\TestProject.sln"'
                
                

            }
        }
        
 stage('Test') { 
            steps {
                bat "mvn test -f TestProject" 
            }
        }
        stage('Deploy') { 
            steps {
                bat "mvn package -f TestProject" 
            }
        }
       
    }

}
