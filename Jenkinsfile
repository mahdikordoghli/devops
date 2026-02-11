pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build') {
            steps {
                sh '/opt/maven/bin/mvn clean compile'
            }
        }

        stage('Package') {
            steps {
                sh '/opt/maven/bin/mvn package'
            }
        }

        stage('Success') {
            steps {
                echo 'Build et Package terminés avec succès !'
            }
        }
    }
}
