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
                sh 'cd simple-java-maven-app'
                 }
        }
        stage('Build'){
            steps{
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
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