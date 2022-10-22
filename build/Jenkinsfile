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
git config user.name \'Jenkis-CI\'
git config user.email \'mstiesto01@gmail.com\'
git add build/* && git commit -am "[Jenkins CI] Add build file"'''
      }
    }

    stage('Push to Github Registry') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh 'echo Jenkins-CI pushing '
          sh 'git push origin -u gh-pages'
        }

      }
    }

  }
}