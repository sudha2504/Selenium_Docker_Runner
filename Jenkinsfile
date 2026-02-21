pipeline {
    agent any
    
    parameters {
      choice choices: ['firefox', 'chrome'], description: 'Select the Browser', name: 'BROWSER'
    }
 
    stages{

         stage('Bring Grid up'){
           steps {
             sh  "docker compose -f grid.yaml up --scale ${params.BROWSER}=2 -d"
           }
         }

         stage('Run Test'){
          steps {
             sh "docker compose -f test-suites.yaml up"
           }
         }
    }

    post{
      always{
         sh  "docker compose -f grid.yaml down"
         sh "docker compose -f test-suites.yaml down"
         archiveArtifacts artifacts: 'output/flight-reservation/emailable-report.html', followSymlinks: false
         archiveArtifacts artifacts: 'output/vendor-portal/emailable-report.html', followSymlinks: false

      }
    }
}
