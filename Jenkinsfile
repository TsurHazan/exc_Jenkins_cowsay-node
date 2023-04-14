node {
    stage('Build and Test') {
        sh 'node --version'
        dir('ops/workspace') {
            sh 'docker-compose up'
        }
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'docker-compose -f ops/workspace/docker-compose.yml run --rm sonar-scanner'
        }
    } 
}

//('-v /var/run/docker.sock:/var/run/docker.sock')
