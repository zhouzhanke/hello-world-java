pipeline {
    agent none
        environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:latest'
                    args '-v ~/.m2:/root/.m2'
                }
            }
            steps {
                sh '''
                    docker --version
                    echo "---------------------------------------------------------------------"
                    echo "Hello P1"
                    mvn --version
                    mvn clean package
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
        stage('P2') {
            agent {
                docker {
                    image 'openjdk:8-jdk'
                }
            }
            steps {
                sh '''
                    echo "---------------------------------------------------------------------"
                    echo "Hello P2 JDK"
                    java -version
                    java HelloWorld
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
    }
}
