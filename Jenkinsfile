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
cd build && git add . && git commit -am "[Jenkins CI] Add build file"'''
      }
    }
    stage('Push Version Back to Git') {
        withCredentials([string(credentialsId: '98e93885-136d-4b37-b95e-0ae963645851', variable: 'TOKEN')]) {
            sh 'echo Jenkins-CI pushing '
            sh 'git config --global push.default simple'
            sh('git push https://mstiesto:${TOKEN}@github.com/mstiesto/mstiesto.github.io.git -u gh-pages')
        }
    }

  }
}
