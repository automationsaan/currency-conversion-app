pipeline {
    agent {
        node {
            label 'maven'
        }
    }

//create environment variable for maven path    
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building...'
                    sh 'mvn clean package'
                }
            }
        }
    }
    stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'sonarqube-scanner'
    }
    steps{
    withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
}
