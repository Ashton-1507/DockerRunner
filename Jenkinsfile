pipeline{
    agent any
    stages{
        stage('Bring Grid up'){
            steps{
                sh "docker-compose -f grid.yaml up -d"
            }
        }
        stage('Bring Grid up'){
            steps{
                sh "docker-compose -f test-suite.yaml up"
            }
        }
    }
    post{
        always{
            sh "docker-compose -f grid.yaml down"
            sh "docker-compose -f test-suite.yaml down"
        }
    }
}