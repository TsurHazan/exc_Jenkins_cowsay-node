node {
    stage('Add Jenkins user to Docker group') {
        sh 'sudo usermod -aG docker jenkins'
    }

    docker.image('docker').inside('-v /var/run/docker.sock:/var/run/docker.sock') {
        stage('Build and Test') {
            sh 'docker-compose -f ./ops/workspace/docker-compose.yml up --build --abort-on-container-exit'
        }

        stage('Code Analysis with SonarQube') {
            withSonarQubeEnv('SonarQube Server') {
                sh 'docker-compose -f ./ops/workspace/docker-compose.yml run --rm sonar-scanner'
            }
        }
    }
}


//('-v /var/run/docker.sock:/var/run/docker.sock')
