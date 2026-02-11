pipeline {
agent any

```
tools {
    maven 'Maven3'      // Nom configuré dans Jenkins (Global Tool Configuration)
    jdk 'JDK17'         // Nom configuré dans Jenkins
}

environment {
    GIT_REPO = 'https://github.com/TON_USERNAME/TON_REPO.git'
    BRANCH = 'main'
}

stages {

    stage('Cloner le code depuis GitHub') {
        steps {
            git branch: "${BRANCH}", url: "${GIT_REPO}"
        }
    }

    stage('Compiler le code') {
        steps {
            sh 'mvn clean compile'
        }
    }

    stage('Build / Package') {
        steps {
            sh 'mvn package'
        }
    }
}

post {
    success {
        echo 'Pipeline exécuté avec succès ✅'
    }
    failure {
        echo 'Echec du pipeline ❌'
    }
}
```

}
