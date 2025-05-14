pipeline {
    agent {
        node {
            label 'maven'
        }
    }

#create environment variable for maven path    
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
}
