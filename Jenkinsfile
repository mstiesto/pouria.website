pipeline {
    agent
    {
        docker
        {
            image 'jekyll/jekyll:3.8'
            args '''
                -u root:root
                -v "${WORKSPACE}:/srv/jekyll"
            '''
        }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    cd /srv/jekyll
                    jekyll --version
                '''
            }
        }
    }
}
