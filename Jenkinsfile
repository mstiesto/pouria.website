pipeline {
  agent any
  stages {
    stage('bubuli') {
      steps {
        sh '''echo \'Installing bundles..\'
bundle install'''
        sh '''echo \'Building..\'
bundle exec jekyll build'''
        git(url: 'github.com/mstiesto/mstiesto.github.io', branch: 'gh-pages', changelog: true)
      }
    }

  }
}