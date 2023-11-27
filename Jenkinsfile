pipeline{
    agent any
    parameters {
         choice  choices: ["Repo"],
                 description: 'Type of scan that is going to perform inside the container',
                 name: 'REPO_NAME'
 
         string defaultValue: "https://github.com/jenkins-docs/simple-java-maven-app.git",
                 description: 'Target Repo to scan',
                 name: 'TARGET'
      }
    stages{
        stage('checkout'){
            steps{
                sh 'rm -rf *'
                checkout scm
                sh 'pwd'
                sh 'echo ${WORKSPACE}'
                 }
        }
        stage('git'){
            steps{
                script {
                        sh """
                            rm -rf * && git clone ${params.TARGET} .
                            """
                                              }
                //sh 'rm -rf *'
                //sh 'git clone https://github.com/jenkins-docs/simple-java-maven-app.git'
                 }
        }
        stage('Build'){
            steps{
              //sh 'mvn clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=squ_64ab57a2a4d9329f633895ef209da970931236d0'
                sh 'cd simple-java-maven-app && mvn -B -Denforcer.skip=true clean package'
                sh 'pwd'
                
            }
        }
        stage('Code Quality'){
            steps{
                sh "cd simple-java-maven-app && mvn -B -Denforcer.skip=true clean install sonar:sonar -Dsonar.projectKey=ganesh -Dsonar.projectName='ganesh' -Dsonar.host.url='http://localhost:9000'  -Dsonar.dependencyCheck.jsonReportPath=target/dependency-check-report.json -Dsonar.dependencyCheck.xmlReportPath=target/dependency-check-report.xml -Dsonar.dependencyCheck.htmlReportPath=target/dependency-check-report.html -Dsonar.token=squ_64ab57a2a4d9329f633895ef209da970931236d0"
            }
        }
        stage('Unit Test'){
            steps{
                sh "cd simple-java-maven-app && mvn -B -Denforcer.skip=true test"
        }
        }
        stage('SAST Dependency Scan') {
        steps {
            sh 'cd simple-java-maven-app && bearer scan .'
            //sh "cd simple-java-maven-app && mvn org.owasp:dependency-check-maven:aggregate"
        }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
        steps {
        sh 'pwd'
        //dependencyCheck additionalArguments: ''' 
        //            -o './'
        //            -s './'
        //            -f 'ALL' 
        //            --nvdApiKey '8379bbff-5498-4b5d-a586-5edb32a75e04'
        //            --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
        
        //dependencyCheckPublisher pattern: 'dependency-check-report.xml'
      }
    }
    
    
    }
}