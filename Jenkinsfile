node {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
    }
    stage('Code Analysis with SonarQube') {
        withSonarQubeEnv('SonarQube Server') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
        }
    } 
}

//Tsur Hazan
