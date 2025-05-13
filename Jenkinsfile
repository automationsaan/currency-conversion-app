pipeline {
    agent {
        node {
            label 'maven'
        }
    }

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

    //     stage('Test') {
    //         steps {
    //             script {
    //                 echo 'Testing...'
    //                 sh 'mvn test'
    //             }
    //         }
    //     }

    //     stage('Deploy') {
    //         steps {
    //             script {
    //                 echo 'Deploying...'
    //                 sh 'mvn deploy'
    //             }
    //         }
    //     }
    // }
}