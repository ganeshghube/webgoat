pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scm
                 }
        }
        stage('git'){
            steps{
                sh 'git clone https://github.com/jenkins-docs/simple-java-maven-app.git'
                 }
        }
        stage('Build'){
            steps{
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
                sh 'cd simple-java-maven-app && mvn -B -DskipTests clean package'
                sh 'pwd'
                
            }
        }
        stage('deploy'){
            steps{
                sh 'pwd'
            }
        }

    }
}