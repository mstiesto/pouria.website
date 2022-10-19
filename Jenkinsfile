pipeline {
  agent {
    node {
      label 'Ruby'
    }

  }
  stages {
    stage('Build') {
      agent any
      steps {
        sh '''echo \'Installing bundles..\'
bundle install'''
        sh '''echo \'Building..\'
bundle exec jekyll build'''
      }
    }

    stage('Deploy') {
      agent any
      steps {
        git(url: 'github.com/mstiesto/mstiesto.github.io', branch: 'gh-pages', changelog: true)
      }
    }

  }
}