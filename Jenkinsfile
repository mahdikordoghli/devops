pipeline {
    agent any

    tools {
        maven 'Maven3'    // Name of Maven in Jenkins global config
        // jdk 'JDK17'    // Uncomment and replace if you configured a JDK tool
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
                    def mvnHome = tool 'Maven3'
                    sh "${mvnHome}/bin/mvn clean compile"
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    def mvnHome = tool 'Maven3'
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






