pipeline {
  agent any

  stages {
    stage ('one') {
      steps {
        sh '''docker kill httpd_s1 || true
        docker rm httpd_s1 || true
        cp index.html /var/lib/docker/volumes/A1/_data/
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
