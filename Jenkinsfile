pipeline {
    agent any
    stages {
        stage('zip') {
            steps {
//               sh "aws configure set region $AWS_DEFAULT_REGION" 
//               sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
//               sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
                 sh "pwd"  
                 dir ("/var/lib/jenkins/workspace"){
                    sh "zip -r rent-app.zip rent-app"}
            }  
        }
        stage("Upload"){
            steps{
                  dir ("/var/lib/jenkins/workspace"){
                  sh "/var/lib/jenkins/workspace/aws-python/bin/python3 s3-upload-script.py"}
                }    
            }
        
        }
   } 
