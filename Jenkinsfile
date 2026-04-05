pipeline {
    agent any

    tools {
        maven 'mymaven'
    }

    environment {
        NAME = 'Dhanush'
    }

    parameters {
        choice choices: ['dev', 'prod'], description: 'select environment', name: 'select_env'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests=true'
                
            }
        }

        stage('Parallel Tests') {
            parallel {

                stage('Test A') {
                    agent {label 'Slave01'}
                    steps {
                        echo 'Running Test A'
                        sh 'mvn test'
                    }
                }

                stage('Test B') {
                    agent {label 'Slave02'}
                    steps {
                        echo 'Running Test B'
                        sh 'mvn test'
                    }
                }

            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}