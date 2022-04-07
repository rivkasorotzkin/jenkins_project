pipeline {
   agent any
   stages {
    stage('Checkout') {
steps{
    Download_Repositories()
    dir("${WORKSPACE}/code"){
        sh '''
            ls -ltr code/playbooks/
            git diff --name-only --diff-filter=M @~ > list.csv
            '''
    }
}
    }
  }
}
