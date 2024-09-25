pipeline {
    agent any

    stages {
        stage('Git cloning') {
            steps {
                git url: 'https://github.com/moazsys/Angular-HelloWorld.git', branch: 'main'
            }
        }
        stage('Install Dependencies') {
            steps {
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
                
            
                    def remoteHost = 'moaznaeem@4.161.47.69'
                    def remoteDir = "/home/moaznaeem/dep"
                    sh "scp -r dist/Angular-HelloWorld/* ${remoteHost}:${remoteDir}"
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
