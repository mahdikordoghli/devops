pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-21-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
        MAVEN_HOME = "/opt/maven"
    }

    stages {
        stage('Compile & Test') {
            steps {
                sh '${MAVEN_HOME}/bin/mvn clean install -DskipTests'
            }
        }
    }
}
