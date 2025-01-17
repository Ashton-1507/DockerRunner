pipeline{
    agent any
    stages{
        stage('Grid up'){
            steps{
                sh "docker-compose -f grid.yaml up -d"
            }
        }
        stage('test-suite up'){
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