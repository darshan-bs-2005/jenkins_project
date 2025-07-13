pipeline {
    agent {
        docker {
            image 'python:3.10-slim'
        }
    }
    stages {
        stage('Clone HTML Game') {
            steps {
                git 'https://github.com/darshan-bs-2005/jenkins_project.git'
            }
        }
        stage('Serve HTML') {
            steps {
                sh '''
                    mkdir -p /tmp/game
                    cp index.html /tmp/game/
                    cd /tmp/game
                    nohup python3 -m http.server 8000 --bind 0.0.0.0 &
                    sleep 120
                '''
                echo 'Site is live for 2 minutes at http://<EC2-IP>:8000'
            }
        }
    }
}

