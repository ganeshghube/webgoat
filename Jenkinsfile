pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                sh 'git clone https://github.com/ganeshghube/javasample.git'
            }
        }
        stage('Build'){
            steps{
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
            sh 'cd java-hello-world-with-maven-master'
            sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('deploy'){
            steps{
                sh 'pwd'
            }
        }

    }
}