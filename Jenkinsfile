pipeline {
  agent any
  stages {
    stage('build') {
      agent any
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