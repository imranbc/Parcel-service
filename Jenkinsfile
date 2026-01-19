
pipeline {
    //agent { label 'node1' }
     agent any
 // environment {
 //        JFROG_USER = credentials('jfrog-creds').username
 //        JFROG_API_KEY = credentials('jfrog-creds').password
 //    }
    stages {

        stage('Checkout') {
            steps {
                git branch: 'feature-1',
                    url: 'https://github.com/imranbc/Parcel-service.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                    java -version
                    mvn -version

                    export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))
                    export PATH=$JAVA_HOME/bin:$PATH
                    echo "JAVA_HOME=$JAVA_HOME"
                    echo "PATH=$PATH"

                    mvn clean install
                '''
            }
        }
        stage('publish') {
            steps {
                sh '''
                   mvn clean deploy
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                whoami
                '''
                // mvn spring-boot:run
            }
        }
    }
}
