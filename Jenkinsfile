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

    stage('Commit') {
      steps {
        sh '''git checkout -B gh-pages
git config user.name \'mstiesto\'
git config user.email \'mstiesto01@gmail.com\'
cd build && git add . && git commit -am "[Jenkins CI] Add build file"'''
      }
    }

    stage('Push') {
      environment {
        GIT_AUTH = 'credentials(\'jenkins\')'
      }
      steps {
        sh 'git push origin -u gh-pages'
      }
    }

  }
}