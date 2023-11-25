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
                sh 'rm -rf *'
                sh 'git clone https://github.com/jenkins-docs/simple-java-maven-app.git'
                 }
        }
        stage('Build'){
            steps{
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_39020d60b148d7150705032eb64cb1d7f4a0699e'
                sh 'cd simple-java-maven-app && mvn -B -Denforcer.skip=true clean package'
                sh 'pwd'
                
            }
        }
        stage('Code Quality'){
            steps{
                sh "cd simple-java-maven-app && mvn -B -Denforcer.skip=true clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url='http://localhost:9000'  -Dsonar.dependencyCheck.jsonReportPath=target/dependency-check-report.json -Dsonar.dependencyCheck.xmlReportPath=target/dependency-check-report.xml -Dsonar.dependencyCheck.htmlReportPath=target/dependency-check-report.html -Dsonar.token=squ_e5d85d6ce1dbdb221b8dca60299952e7ce63a28d"
            }
        }
        stage('Unit Test'){
            steps{
                sh "cd simple-java-maven-app && mvn -B -Denforcer.skip=true test"
        }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
        steps {
        //sh "cd simple-java-maven-app && mvn org.owasp:dependency-check-maven:aggregate"
        }
        }
    
    
    }
}