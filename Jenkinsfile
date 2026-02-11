pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build & Package') {
            steps {
                // Directly set JAVA_HOME and PATH in the shell
                sh '''
                export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
                export PATH=$JAVA_HOME/bin:/opt/maven/bin:$PATH

                # Verify Java & Maven versions
                java -version
                mvn -version

                # Build and package
                mvn clean install -DskipTests
                mvn package -DskipTests
                '''
            }
        }

        stage('Success') {
            steps {
                echo 'Build and package completed successfully!'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
        failure {
            echo 'Build failed! Check the logs above.'
        }
    }
}
