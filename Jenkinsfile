node {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
            sh 'docker stop $(docker ps -q --filter ancestor=cowsay)'
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('my-default-config') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
            sh 'docker stop cowsaydocker stop $(docker ps -q --filter ancestor=cowsay)'
        }
    } 
}

//Tsur Hazan
