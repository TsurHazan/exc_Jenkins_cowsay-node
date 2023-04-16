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
            sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=cowsay \
  -Dsonar.projectName='cowsay' \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.token=sqp_6e3498f909eb7f81d06f10c609b9bd14daa860f3'
            sh 'node --version'
            checkout scm
            sh 'docker build -t cowsay .'
            sh 'docker run --rm -d -p 9100:8080 cowsay'
            sh 'docker stop $(docker ps -q --filter ancestor=cowsay)'
        }
    } 
}

//Tsur Hazan
