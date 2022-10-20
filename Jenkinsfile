pipeline {
  agent {
    docker {
      image 'jekyll/jekyll:3.8'
      args '''-u root:root
-v "${WORKSPACE}:/srv/jekyll"'''
    }

  }
  stages {
    stage('Biuld') {
      steps {
        sh 'jekyll build --destination ./build'
      }
    }

    stage('Deploy') {
      steps {
        git(url: 'https://github.com/mstiesto/mstiesto.github.io', branch: 'gh-pages', changelog: true)
      }
    }

  }
}