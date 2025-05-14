pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    // Create environment variable for Maven path
    environment {
        PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo "----------- build started ----------"
                    sh 'mvn clean package'
                    echo "----------- build completed ----------"
                }
            }
        }

    stage('Test') {
            steps {
                script {
                    echo "----------- unit test started ----------"
                    sh 'mvn surefire-report:report'
                    echo "----------- unit test Complted ----------"
                }
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarqube-scanner'
            }
            steps {
                withSonarQubeEnv('sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    } 
} 
