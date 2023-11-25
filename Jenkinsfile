pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                git branch: 'main', changelog: false, credentialsId: 'gitscm', poll: false, url: 'https://github.com/ganeshghube/javasample.git'
            }
        }
        stage('Build and Code Quality'){
            steps{
              sh 'pwd'
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
            }
        }
        stage('deploy'){
            steps{
                sh 'pwd'
            }
        }

    }
}