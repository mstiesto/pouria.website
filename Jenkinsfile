pipeline {
    agent any

    stages {

		stage('Install Bundles') {
            steps {
                echo 'Installing bundles..'
sh 'bundle install --path ~/.gem'
            }
        }
        stage('Building site') {
            steps {
                echo 'Building..'
sh 'bundle exec jekyll build'
            }
        }
        stage('Deploy') {
			when {
                branch 'dev'
            }
            steps {
                echo 'Deploying to dev....'
sh 'git add ./build && git push origin -u gh-pages
            }
			
			when {
                branch 'main'
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}
