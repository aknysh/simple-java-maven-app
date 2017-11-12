pipeline {
    agent any
    stages {
        stage('Install Maven') {
            steps {
                sh 'echo $(which mnv)'
            }
        }
         stage('Validate') {
             steps {
                 sh '$(which mnv) validate'
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
