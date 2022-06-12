pipeline {
  agent {
    label 'jenkins-slave-java'
  }
  stages {
    stage('Show Parameters'){
        currentBuild.displayName = "${BUILD_NUMBER}.${GIT_COMMIT}"
    }
    stage('Build'){
        steps{
            sh 'mvn package'
        }
    }
  }
  post {
    always {
      echo "Job execution complete."
    }
    success {
      archiveArtifacts artifacts: 'target/*'
    }
    unsuccessful {
      echo "Job execution status is failed, please check error logs"
    }
    cleanup {
      echo 'Cleaning up environment'
      sh 'rm -rf maven-example'
    }
  }
}