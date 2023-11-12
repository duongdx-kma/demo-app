pipeline {
    agent {
        node {
            label 'docker-agent-alpine'
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Build step ...'
            }
        }
        stage('Test') {
            steps {
                echo 'Test step ...'
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver step ...'
            }
        }
    }
}

