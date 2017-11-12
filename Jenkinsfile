pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
       stage('Validate') {
         steps {
             sh 'mvn validate'
         }
       }
       stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
