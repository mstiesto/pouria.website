pipeline {
  agent {
    docker {
      image 'jekyll/jekyll:3.8'
      args '''-u root:root
-v "${WORKSPACE}:/usr/local/bundle"'''
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
        sh '''cd git && git add . && git commit -m "Update blog from Jenkins"
git subtree push --prefix build origin gh-pages'''
      }
    }

  }
}