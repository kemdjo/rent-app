pipeline {
    agent any
    stages {
        stage('deploy') {
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
                withAWS(region:"${AWS_DEFAULT_REGION}", credentials:"${AWS_ACCESS_KEY_ID}){
                    s3Upload(file:"rent-app.zip", bucket:"motsebo-rentzon-web-file", path:"$/var/lib/jenkins/workspace/rent-app.zip")
                }    
            }
        
        }
    }
}  
