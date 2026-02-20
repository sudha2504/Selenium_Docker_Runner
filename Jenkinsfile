pipeline {
    agent any

    stages{

         stage('Run test'){
           steps {
             sh  "docker compose up"
           }
         }

         stage('Bring Grid down'){
          steps {
             sh "docker compose down"
           }
         }
    }
}