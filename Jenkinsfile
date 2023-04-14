node {
    stage('Build and Test') {
        sh 'node --version'
        dir('ops/workspace') {
            sh 'pwd'
            sh 'docker compose -f /home/tsurhazan/exercises/week_3/Jenkins/cowsay/exc_Jenkins_cowsay-node/ops/workspace/docker-compose.yml up'
        }
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'docker-compose -f ops/workspace/docker-compose.yml run --rm sonar-scanner'
        }
    } 
}

//('-v /var/run/docker.sock:/var/run/docker.sock')
