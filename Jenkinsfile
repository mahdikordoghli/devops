pipeline {
    agent any

    tools {
        maven 'Maven3' // Nom du Maven configuré dans Jenkins
        jdk 'JDK17'    // Nom du JDK configuré dans Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Success') {
            steps {
                echo 'Build et Package terminés avec succès !'
            }
        }
    }
}



