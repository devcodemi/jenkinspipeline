pipeline {
    agent any
    tools{
      maven 'localMaven'
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deployment') {
          steps {
            build job: 'deploy-to-staging'
          }
        }
    }
}
