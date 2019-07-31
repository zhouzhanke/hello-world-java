pipeline {
    agent any
    stages {
        stage('Build') {
            agent { docker { image 'maven:3.3.3' }}
            steps {
                echo "--------------------------------------------------"
                sh 'mvn --version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                    echo "--------------------------------------------------"
                '''
            }
        }
        stage('Build') {
            agent { docker { image 'openjdk:8-jre' }}
            steps {
                sh '''
                    echo "--------------------------------------------------"
                    echo "Hello JDK"
                    java -version
                    Javac HelloWorld.java
                    Java HelloWorld
                    echo "--------------------------------------------------"
                '''
            }
        }
    }
}
