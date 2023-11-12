pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Build step ...'
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test step ...'
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
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

