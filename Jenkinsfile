pipeline {
    agent { docker 'maven:3.3.3' }
    stages {
        stage('Build') {
            steps {
                agent { docker 'maven:3.3.3' }
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
            steps {
                agent { docker 'openjdk:8-jre'  }
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
