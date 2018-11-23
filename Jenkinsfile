pipeline {
    agent any 
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/awspipeline/spring-petclinic.git'
 
            }
        }
        stage('Build') { 
            steps {
          
                 sh 'mvn clean package'
            }
        }
        
        stage ('Junit') {
            steps {
                 junit 'target/surefire-reports/*.xml'
            }
        }

      stage ('s3 deploy')  {
      
             steps {
                 s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'demo985', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '**/*.jar', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 'bucket', userMetadata: []
                 
             }
            }
            
        }
    }

       
    
