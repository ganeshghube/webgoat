pipeline{
    stages{
        stage('checkout'){
            steps{
                sh 'rm -rf *'
				sh 'git clone https://github.com/ganeshghube/webgoat.git'
            }
        }
        stage('build and code-quality'){
            steps{
               sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000           -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
            }
        }
        stage('scan'){
            steps{
                sh 'pwd'
            }
        }
        
    }
}
