pipeline {
  agent {
    label 'swarm-agent'
  }
  environment {
     PROJECT_NAME   = "jenkins-master"
     BUILD_REGISTRY = "internal-hostname.com"
     SECONDARY_REG  = "secured-registry.com"
  }
  stages {
    stage('Docker Build') {
      steps {
        script {
          DOCKER_IMAGE1 = "${BUILD_REGISTRY}/${PROJECT_NAME}"
          DOCKER_IMAGE2 = "${SECONDARY_REG}/$PROJECT_NAME}"
          sh "docker build -t ${DOCKER_IMAGE1}:${BUILD_NUMBER} -t ${DOCKER_IMAGE2}:${BUILD_NUMBER} -t ${DOCKER_IMAGE2}:latest ."
        }
      }
    }

    stage('Push to Registry') {
      steps {
        
       /* sh """
           docker push ${DOCKER_IMAGE1}:${BUILD_NUMBER}
           docker push ${DOCKER_IMAGE2}:${BUILD_NUMBER}
           docker push ${DOCKER_IMAGE2}:latest
        """
       */
       echo "Push currently disabled"
      }
    }
  }
}

