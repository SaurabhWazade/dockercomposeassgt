pipeline {
  agent any

  stages {
    stage ('one') {
      steps {
        sh '''docker kill httpd_s3 || true
        docker rm httpd_s3 || true
        cp index.html /var/lib/docker/volumes/A3/_data/
        docker-compose up -d
        docker exec -d root-httpd_s3-1 sh -c "chmod 644 /usr/local/apache2/htdocs/index.html"
        docker exec -d root-httpd_s1-1 sh -c "chmod 644 /usr/local/apache2/htdocs/index.html"
        docker exec -d root-httpd_s2-1 sh -c "chmod 644 /usr/local/apache2/htdocs/index.html"
        '''
      }
    }
  }
  post {
    always {
      sh "rm -rf ${WORKSPACE}/*"
    }
  }
}
