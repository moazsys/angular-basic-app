pipeline {
    agent any

    stages {
        stage('Install Dependencies')
      {
            steps 
        {
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                sh 'ng build --configuration production'
            }
        }
        stage('Deploy') 
        {
            steps
            {
                script
                {
                
            
                    def remoteHost = 'moazn@4.216.187.218'
                    def remoteDir = "/home/moazn/dep"
                    sh "scp -r dist/angular-basic-app/* ${remoteHost}:${remoteDir}"
                }
            }
        }
        
    }

    post {
        success {
            echo 'Deployment completed successfully.'
        }
        failure {
            echo 'Deployment failed. Check the logs.'
        }
    }
}
