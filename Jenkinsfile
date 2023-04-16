node {
        stage('Build and Test') {
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
            sh 'docker stop $(docker ps -q --filter ancestor=cowsay)'
    }
    stage('Code Analysis with SonarQube') {
        def scannerHome = tool 'SonarQube 4.8.0.2856';
        withSonarQubeEnv('my-default-config') {
            sh "${scannerHome}/bin/sonar-scanner"
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
            sh 'docker stop $(docker ps -q --filter ancestor=cowsay)'
        }
    } 
}

//Tsur Hazan
