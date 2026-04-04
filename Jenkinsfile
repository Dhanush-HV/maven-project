pipeline {
    agent any

    tools {
        maven 'mymaven'
    }
    environment {
        NAME = 'Dhanush'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo 'hello $NAME, your build is succesfuly executed'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}