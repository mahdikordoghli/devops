pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/temurin-21-jdk-amd64" // Use the actual JDK directory
        PATH = "${JAVA_HOME}/bin:/opt/maven/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build & Package') {
            steps {
                sh '''
                    echo "JAVA_HOME = $JAVA_HOME"
                    java -version
                    mvn -version

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
