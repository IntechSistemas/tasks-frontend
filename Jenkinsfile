pipeline {
    agent any
    parameters {
        choice(
            choices: ['deployPre', 'deployPro'],
            description: 'Escolha',
            name: 'REQUESTED_ACTION'
        )
    }
    stages {
        stage ('Build') {
            when {
                expression { params.REQUESTED_ACTION == 'deployPre'}    
            }
            steps {
         
                bat 'mvn clean package -DskipTests=true'
            }
        } 
        stage ('Deploy') {
            when {
                expression { params.REQUESTED_ACTION == 'deployPre'}    
            }
            steps {
                bat 'echo Deploy'
                deploy adapters: [tomcat8(credentialsId: 'tomcat-login', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks', war: 'target/tasks.war'
            }        
        }
        stage ('Prod') {
            when {
                expression { params.REQUESTED_ACTION == 'deployPro'}    
            }
            steps {
         
               echo 'Tentativa em Prod'
            }    
        }
    }
}
