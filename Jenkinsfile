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
        stage('test') {
            agent { docker { image 'openjdk:8-jdk' }}
            steps {
                sh '''
                    echo "--------------------------------------------------"
                    echo "Hello JDK"
                    java -version
                    docker run --rm -v $PWD:/app -w /app demo/oracle-java:8 javac HelloWorld.java
                    docker run --rm -v $PWD:/app -w /app demo/oracle-java:8 java HelloWorld
                    echo "--------------------------------------------------"
                '''
            }
        }
    }
}
