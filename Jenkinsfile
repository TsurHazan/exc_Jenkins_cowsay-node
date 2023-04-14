node {
   // docker.image('node:alpine').inside {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -p 9100:8080 cowsay'
        //}
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -p 9100:8080 cowsay'
        }
    } 
}

//('-v /var/run/docker.sock:/var/run/docker.sock')
//             sh 'sudo docker compose -f /home/tsurhazan/exercises/week_3/Jenkins/cowsay/exc_Jenkins_cowsay-node/ops/workspace/docker-compose.yml up'
