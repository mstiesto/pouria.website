pipeline {
  agent {
    docker {
      image 'jekyll/jekyll:3.8'
      args '''-u root:root
-v "${WORKSPACE}:/srv/jekyll"'''
    }

  }
  stages {
    stage('Prepare') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh '''rm -rf _site
git config --global user.email "mstiesto@gmail.com"
git config --global user.name "Jenkins-CI"
git clone -b gh-pages `git config remote.origin.url` _site'''
        }
      }
    }
    stage('Build') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh '''jekyll build --destination ./_site'''
        }
      }
    }
    stage('Push') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh '''cd ./_site
git add -A
git commit -am "Jenkins-CI"
git push'''
        }
      }
    }
  }
}
