def defaultValgrind = false
if ( JOB_NAME == "OpenGauss_nightly_valgrind" )
{
  defaultValgrind = true
}
pipeline {
  parameters {
    booleanParam (defaultValue: defaultValgrind, name: 'valgrind')
  }
  agent none
  stages {
    stage('build and archive installation') {
      agent {
        label 'build'
      }
      steps {
         echo 'this is the build stage'
         sh 'ls -l'
      }
    }
    stage('run tests') {
      agent {
        label 'test'
      }
      when{
        branch 'main'
      }
      steps {
         sh 'java -version'
         echo 'this is the run stage'
         sh 'make check || true' 
         junit '**/target/*.xml' 
      }
      post {
       always {
          echo 'this is the always stage'
        }
      }
    }
  } 
}
