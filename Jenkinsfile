pipeline {
    agent any

    tools {
        maven 'maven3'    // Nom exact de Maven configuré dans Jenkins
        // jdk 'JDK17'    // Décommente si tu as configuré un JDK
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mahdikordoghli/devops.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Get Maven home from Jenkins tool config
                    def mvnHome = tool 'maven3'
                    sh "${mvnHome}/bin/mvn clean compile"
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    def mvnHome = tool 'maven3'
                    sh "${mvnHome}/bin/mvn package"
                }
            }
        }

        stage('Success') {
            steps {
                echo 'Build et Package terminés avec succès !'
            }
        }
    }
}








