pipeline {
  agent {
    docker {
      image 'jekyll/jekyll:3.8'
      args '''-u root:root
-v "${WORKSPACE}:/srv/jekyll"'''
    }

  }
  stages {
    stage('Build/Push') {
      steps {
        withCredentials(bindings: [gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {
          sh '''rm -rf _site
git clone -b gh-pages `git config remote.origin.url` _site
jekyll build --destination ./_site
cd ./_site
git add -A
git commit -am "Jenkins-CI"
git push'''
        }

      }
    }

  }
}