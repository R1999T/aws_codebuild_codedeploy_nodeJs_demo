pipeline {
    agent any
    tools {nodejs "node16"}
    environment{
        NODE_ENV = "production"
    }
    
    
    
    stages {
        stage('source') {
            steps {
                git 'https://github.com/R1999T/aws_codebuild_codedeploy_nodeJs_demo.git'
                echo 'index.js file content'
                sh 'cat index.js'
            }
        }
        stage('build') {
            environment{
                NODE_ENV= "staging"
            }
            steps {
                withCredentials([string(credentialsId: '00808065-378b-4116-bbbb-fdbcab5cda12', variable: 'secvar')]) {
                // some block
                echo secvar
                }
                
                sh 'npm install'
            }
        }
        stage('saveArtifacts') {
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
    }
}
