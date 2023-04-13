node {
    docker.image('docker').inside {
        stage('Build and Test') {
            sh 'cd ~/exercises/week_3/Jenkins/cowsay/exc_Jenkins_cowsay-node/ops/workspace/'
            sh 'pwd'
            sh 'docker-compose up'
        }

        stage('Code Analysis with SonarQube') {
            withSonarQubeEnv('SonarQube Server') {
                sh 'docker-compose -f ~/exercises/week_3/Jenkins/cowsay/exc_Jenkins_cowsay-node/ops/workspace/ run --rm sonar-scanner'
            }
        }
    }
}


//('-v /var/run/docker.sock:/var/run/docker.sock')
