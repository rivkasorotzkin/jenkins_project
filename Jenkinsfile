pipeline {
   agent any
   stages {
       stage('write') {
           steps {
               script {
                   def date = new Date()
                   def data = "Hello World\nSecond line\n" + date
                   writeFile(file: 'zorg.txt', text: data)
                   sh "ls -l"
                   call "D:\\bin\\gatling.bat"
                   GIT_COMMIT_EMAIL = sh (
                   script: 'git --no-pager show -s --format=\'%ae\'',
                   returnStdout: true
                   ).trim()
                   echo "Git committer email: ${GIT_COMMIT_EMAIL}"
               }
           }
       }
       stage('read') {
           steps {
               script {
                   def data = readFile(file: 'zorg.txt')
                   println(data)
               }
           }
       }
   }
}
