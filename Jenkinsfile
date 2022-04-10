// pipeline {
//    agent any
//    stages {
//        stage('write') {
//            steps {
//                script {
//                    def date = new Date()
//                    def data = "Hello World\nSecond line\n" + date
//                    writeFile(file: 'zorg.txt', text: data)
//                    sh "ls -l"
//                }
//            }
//        }
//        stage('read') {
//            steps {
//                script {
//                    def data = readFile(file: 'zorg.txt')
//                    println(data)
//                }
//            }
//        }
//    }
// }
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
         git clone https://github.com/mergebase/log4j-detector.git
         sh 'ls -l'
      }
    }
    stage('run tests') {
      agent {
        label 'test'
      }
      when{
        branch 'master'
      steps {
         sh 'java -version'
         echo 'this is the run stage'

      }
      post {
        always {
           echo 'this is the always stage'

        }
      }
    }
  }
}

