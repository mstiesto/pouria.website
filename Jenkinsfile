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
git config user.name \'JenkinsCI\'
git config user.email \'jenkinsci@users.noreply.github.example.com\'
cd build && git add . && git commit -am "[Jenkins CI] Add build file"'''
      }
    }

    stage('Push') {
      environment {
        GIT_AUTH = 'credentials(\'mstiesto\')'
        GIT_AUTH_USR = 'mstiesto'
        GIT_AUTH_PSW = '123456'
      }
      steps {
        sh '''git config --local credential.helper "!f() { echo username=\\\\$GIT_AUTH_USR; echo password=\\\\$GIT_AUTH_PSW; }; f"
git push origin HEAD:gh-pages'''
      }
    }

  }
}