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
                    image 'maven:3.6.3-openjdk-8'
                    args '-v ~/.m2:/root/.m2'
                }
            }
            steps {
                sh '''
                    docker --version
                    echo "---------------------------------------------------------------------"
                    mvn --version
                    sh 'mvn -B -DskipTests clean package'
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'openjdk:8-jdk'
                }
            }
            steps {
                sh '''
                    echo "---------------------------------------------------------------------"
                    sh 'mvn test'
                    java -version
                    java HelloWorld
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
    }
}
