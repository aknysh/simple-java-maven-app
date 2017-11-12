pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
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
