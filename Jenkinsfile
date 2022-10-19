pipeline {
  agent any
  stages {
    stage('build') {
      agent any
      steps {
        sh '''echo installing...
jekyll build'''
      }
    }

  }
}