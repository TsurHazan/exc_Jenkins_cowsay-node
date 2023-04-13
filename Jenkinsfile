node {
    docker.image('docker').inside {
        stage('Build and Test') {
            cd "~/exc_Jenkins_cowsay-node"
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
