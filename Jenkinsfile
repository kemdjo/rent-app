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
        stage('Upload') {

        dir('/var/lib/jenkins/workspace'){

            pwd(); //Log current directory

            withAWS(region:'$AWS_DEFAULT_REGION',credentials:'$AWS_ACCESS_KEY_ID') {

                 def identity=awsIdentity();//Log AWS credentials

                // Upload files from working directory 'dist' in your project workspace
                s3Upload(bucket:"motsebo-rentzon-web-file", workingDir:'dist', includePathPattern:'**/*');
            }

        };
    }
    }
}  
