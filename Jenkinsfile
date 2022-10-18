pipeline {
  agent any
  stages {
    stage('bubuli') {
      steps {
        sh '''#!/bin/bash -l

echo \'Installing bundles..\'
bundle install'''
        sh '''#!/bin/bash -l

echo \'Building..\'
bundle exec jekyll build'''
        git(url: 'github.com/mstiesto/mstiesto.github.io', branch: 'gh-pages', changelog: true)
      }
    }

  }
}