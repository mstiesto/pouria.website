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
                branch 'develop'
            }
            steps {
                echo 'Deploying to dev....'
sh 'rsync -avzh ./_site/ /var/www/jekyll-dev/
            }
			
			when {
                branch 'master'
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}
