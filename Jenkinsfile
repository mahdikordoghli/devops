pipeline {
    agent any

    environment {
        // Set the JDK for the pipeline
        JAVA_HOME = "/usr/lib/jvm/java-21-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
        MVN_HOME = "/opt/maven"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build') {
            steps {
                // Build project and skip tests
                sh '''
                export JAVA_HOME=${JAVA_HOME}
                export PATH=$JAVA_HOME/bin:$PATH
                ${MVN_HOME}/bin/mvn clean install -DskipTests
                '''
            }
        }

        stage('Package') {
            steps {
                // Package the app (jar/war)
                sh '''
                export JAVA_HOME=${JAVA_HOME}
                export PATH=$JAVA_HOME/bin:$PATH
                ${MVN_HOME}/bin/mvn package -DskipTests
                '''
            }
        }

        stage('Success') {
            steps {
                echo 'Build and Package completed successfully!'
            }
        }
    }

    post {
        always {
            // Archive artifacts (optional)
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
        failure {
            echo 'Build failed! Check the logs above.'
        }
    }
}
