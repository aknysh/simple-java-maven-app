pipeline {
    agent any
    stages {
       stage('Build') {
            steps {
                sh 'echo $(which mnv) -B -DskipTests clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'echo $(which mnv) test'
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
