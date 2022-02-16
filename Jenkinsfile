pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        } 
        stage ('Deploy') {
            steps {
                bat 'echo Deploy'
                deploy adapters: [tomcat8(credentialsId: 'tomcat-login', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks', war: 'target/tasks.war'
            }
        }
    }
}
