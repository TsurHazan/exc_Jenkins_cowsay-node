node {
   // docker.image('node:alpine').inside {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -p 9100:8080 cowsay'
            sh 'docker stop cowsay'
        //}
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -p 9100:8080 cowsay'
            sh 'docker stop cowsay'
        }
    } 
}

//Tsur Hazan
