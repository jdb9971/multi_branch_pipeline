pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jdb9971/multi_branch_pipeline.git']]])
            }
        }
        stage('Build') {
            steps {
                git 'https://github.com/jdb9971/multi_branch_pipeline.git'
                bat 'python main.py'
                
            }
        }
        stage('Test') {
            steps {
                echo 'The job has been done'
            }
        }
        
    }
    
    post {
        failure {
             emailext attachLog: true, body: 'Testing has been succesfull, pls check it !!', subject: 'success !!!! ', to: 'joydebayan@gmail.com'
  } 
}

}
