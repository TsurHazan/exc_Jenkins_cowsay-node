node {
   // docker.image('node:alpine').inside {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker compose -f ops/workspace/docker-compose.yml up'
         //   sh 'docker build -t cowsay .'
         //   sh 'docker run --rm -p 8080:8080 cowsay'
        //}
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'docker-compose -f ops/workspace/docker-compose.yml run --rm sonar-scanner'
        }
    } 
}

//('-v /var/run/docker.sock:/var/run/docker.sock')
//             sh 'sudo docker compose -f /home/tsurhazan/exercises/week_3/Jenkins/cowsay/exc_Jenkins_cowsay-node/ops/workspace/docker-compose.yml up'
