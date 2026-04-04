pipeline {
    agent any

    tools {
        maven 'mymaven'
    }

    environment {
        NAME = 'Dhanush'
    }

    parameters {
        string(name: 'name', defaultValue: 'DhanushDevang', description: 'Enter your name')
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo "Hello ${env.NAME}, your build is successfully executed, ${params.name}!"
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}