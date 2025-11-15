pipeline {
  agent any

  stages {
    stage ('one') {
      steps {
        sh '''docker kill httpd_s2 || true
        docker rm httpd_s2 || true
        cp index.html /var/lib/docker/volumes/A2/_data/
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
