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
          sh '''echo Pulling gh-pages branch into _site directoy
rm -rf _site'''
          sh 'git clone -b gh-pages `git config remote.origin.url` _site'
        }

      }
    }

    stage('build') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh 'cd ./_site'
          sh '''git config --global user.email "mstiesto01@gmail.com"
git config --global user.name "Jenkins-CI"'''
          sh 'git add -A'
          sh 'git commit -am "Jenkins-CI"'
          sh 'git push'
        }

        sh 'jekyll build --destination ./_site'
      }
    }

  }
}