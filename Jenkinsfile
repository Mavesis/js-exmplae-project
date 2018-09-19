pipeline {
  agent any
  environment {
     def scannerHome = tool 'SonarQube 3.2'
   }
  stages {
      stage('FASE 1 SMC '){
        steps{
          echo'           ------------------------------------------------  COMENZANDO LA DESCARGA DEL PROYECTO  ------------------------------------------------                        '
          git 'https://github.com/Mavesis/js-exmplae-project.git'
        }
      }
    //   stage('FASE 2 SMC '){
    //     steps{
    //       echo'           ------------------------------------------------  COMENZANDO LA CONSTRUCCIÓN DEL PROYECTO  ------------------------------------------------                        '
    //       bat 'mvn clean install'
    //       archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
    //     }
    //  }
      stage('FASE 2 ANALYSIS JS '){
        steps{
          echo'           ------------------------------------------------  COMENZANDO ANÁLISIS DEL PROYECTO   ------------------------------------------------                        '
          echo scannerHome
          echo BRANCH_NAME
          
          withSonarQubeEnv('local_sonar'){
            
            bat "\"${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ProyectoJS -Dsonar.organization=mavesis-github -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=39acfca66c299343b8ac4427b69b5cb78db97cf1 -Dsonar.branch.name=${BRANCH_NAME}\""
          }
        }
      }
  }
}