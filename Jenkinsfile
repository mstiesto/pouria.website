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
        sh '''                    git checkout -B gh-pages
                    git config user.name \'JenkinsCI\'
                    git config user.email \'jenkinsci@users.noreply.github.example.com\'
                    cd build && git add . && git commit -am "[Jenkins CI] Add build file"'''
      }
    }

    stage('Push') {
      steps {
        sh 'git push origin HEAD:gh-pages'
      }
    }

  }
}