pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh '''
                mvn compile  
                mvn exec:java -Dexec.mainClass="com.vineetmanohar.module.Main"  
                '''
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
    }
}
