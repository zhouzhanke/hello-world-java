pipeline {
    agent none
        environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    stages {
        stage('P1') {
            agent {
             docker {
              image 'maven:3.3.3',
              image 'docker:latest'
               }}
            steps {
                sh '''
                    echo "---------------------------------------------------------------------"
                    echo "Hello P1"
                    mvn --version
                    javac HelloWorld.java
                    java HelloWorld
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
        stage('P2') {
            agent {
             docker {
              image 'openjdk:8-jdk',
              image 'docker:latest'
               }}
            steps {
                sh '''
                    echo "---------------------------------------------------------------------"
                    echo "Hello P2 JDK"
                    java -version
                    javac HelloWorld.java
                    java HelloWorld
                    echo "---------------------------------------------------------------------"
                '''
            }
        }
    }
}
