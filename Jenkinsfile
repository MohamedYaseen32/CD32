pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '27836658-a8b3-41a0-892f-8dcb93a3fcd8', path: '', url: 'http://localhost:8080/')], contextPath: '/CD-JK', war: '**/*.war'
 }
 }
 }
}
