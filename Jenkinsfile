pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
    }
    
    environment {
        USED_RAM=`free -m | grep Mem | awk {'print $3'}`
    }

    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('fetching code') {
            steps {
                git branch: 'master', url: 'https://github.com/duongdx-kma/demo-app.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build step ...'
                sh '''
                cd my-app
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test step ...'
                sh '''
                cd my-app
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            },
            post {
                success {
                    echo 'Archiving artifacts now'
                    archiveArtifacts artifacts: '**/*.txt'
                }
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver step okkkkkkk...'
                sh '''
                FREE_RAM=`free -m | grep Mem | awk '{print $4}'`
                echo "free ram = $FREE_RAM"
                '''
            }
        }
    }
}

