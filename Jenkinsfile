pipeline {
    agent any

    stages{

         stage('Bring Grid up'){
           steps {
             sh  "docker compose -f grid.yaml up"
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

      }
    }
}