pipeline {
  agent any

  stages {
    stage ('one') {
      steps {
        sh '''docker kill httpd_s3 || true
        docker rm httpd_s3 || true
        cp /root/.jenkins/workspace/a3/index.html /var/lib/docker/volumes/A3/_data/
        docker-compose up -d --network=velocity
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
