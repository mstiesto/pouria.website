pipeline {
  agent {
    node {
      label 'Ruby'
    }

  }
  stages {
    stage('Build') {
      agent {
        node {
          label 'jenkins-agent'
        }

      }
      steps {
        sh '''echo \'Installing bundles..\'
bundle install'''
        sh '''echo \'Building..\'
bundle exec jekyll build'''
      }
    }

    stage('Deploy') {
      steps {
        git(url: 'github.com/mstiesto/mstiesto.github.io', branch: 'gh-pages', changelog: true)
      }
    }

  }
}