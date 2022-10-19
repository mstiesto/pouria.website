pipeline {
  agent none
  stages {
    stage('build') {
      environment {
        name = 'jekyll'
      }
      steps {
        sh '''echo installing...
bundell install'''
      }
    }

  }
}