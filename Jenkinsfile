
// BRANCH_NAME --> Es la variable de Jenkins de donde podemos obtener el nombre de la rama.

pipeline {
  agent any
  //Es necesario declarar todas las variables dentro de enviroment{}
  environment {
      // guardamos en una variable la ruta del scanner al que hemos llamado dentro de Jenkins "SonarQube 3.2"
     def scannerHome = tool 'SonarQube 3.2'
   }
  stages {
      stage('FASE 1: CHECKOUT'){
        steps{
          echo'           ------------------------------------------------  COMENZANDO LA DESCARGA DEL PROYECTO  ------------------------------------------------                        '
          git 'https://github.com/Mavesis/js-exmplae-project.git'
        }
      }
      stage('FASE 2: BUILD'){}
      stage('FASE 2: ANALYSIS'){
        steps{
          echo'           ------------------------------------------------  COMENZANDO ANÁLISIS DEL PROYECTO   ------------------------------------------------                        '
          
          withSonarQubeEnv('local_sonar'){ //preparamos el entorno para el análisis de sonar
            
            // Es importante poner bien los escapes para que sea posible ejecutar el scanner.
            bat "\"${scannerHome}\\bin\\sonar-scanner\" -Dsonar.projectKey=ProyectoJS -Dsonar.organization=mavesis-github -Dsonar.sources=. -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=39acfca66c299343b8ac4427b69b5cb78db97cf1 -Dsonar.branch.name=${BRANCH_NAME}"
          }
        }
      }
  }
}