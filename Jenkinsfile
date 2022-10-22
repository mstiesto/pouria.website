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
   
    stage('Push to Github Registry'){
        steps {
            withCredentials([gitUsernamePassword(credentialsId: 'Jenkins', variable: 'TOKEN')]) {                
            sh 'echo Jenkins-CI pushing '
            sh 'git config --global push.default simple'
            sh('git push https://${TOKEN}@github.com/mstiesto/mstiesto.github.io.git -u gh-pages')            
        }            
      }  
    }
    
    
    
    
    
withCredentials([gitUsernamePassword(credentialsId: 'my-credentials-id', gitToolName: 'git-tool')]) {
  sh 'git fetch --all'
}
    
    
    
    
    
    
    
    
    
    
    
  }
}
