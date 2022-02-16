pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                bat 'echo Checkout'
            }
        }
        stage ('Build') {
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Deploy') {
            steps {
                bat 'echo Deploy'
            }
        }
            
    }
}
