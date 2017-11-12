pipeline {
    agent any
    stages {
       stage('Build') {
            steps {
                sh '$(which mnv) -B -DskipTests clean install'
            }
        }
        stage('Test') {
            steps {
                sh '$(which mnv) test'
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
