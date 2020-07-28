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
                    image 'maven:3.6.3'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                sh '''
                    mvn --version
                    javac HelloWorld.java
//                     sh 'mvn -B -DskipTests clean package'
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
//                     sh 'mvn test'
                    java -version
                    java HelloWorld
                '''
            }
        }
    }
}
