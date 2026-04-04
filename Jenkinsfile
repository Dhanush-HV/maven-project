pipeline {
    agent any



    tools {
        maven 'mymaven'
    }
    environment {
        NAME = 'Dhanush'
    }
    parameters {
         string defaultValue: 'DhanushDevang', name: 'name'
}

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
                echo 'hello $NAME, your build is succesfuly executed,${params.name}!'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}