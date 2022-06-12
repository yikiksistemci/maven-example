pipeline {
  agent {
    label 'jenkins-slave-java'
  }
  stages {
    // stage('Prepare environment') {
    //   steps {
    //     sh 'apk add git'
    //   }
    // }
    // stage('Clone code from Git') {
    //   steps {
    //     sh 'git clone https://github.com/yikiksistemci/maven-example.git'
    //   }
    // }

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