pipeline{
    agent any

    parameters {
        choice choices: ['chrome', 'firefox'], description: 'Please select the browser', name: 'BROWSER'
    }

    stages{
        stage('Grid up'){
            steps{
                sh "docker-compose -f grid.yaml up --scale ${params.BROWSER}=2 -d"
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
            archiveArtifacts artifacts: 'output/flight/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'output/vendor/emailable-report.html', followSymlinks: false
        }
    }
}