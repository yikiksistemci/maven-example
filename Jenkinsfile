pipeline {
  agent {
    label 'jenkins-slave-java'
  }
  stages {
    stage('Prepare environment') {
      steps {
        sh 'apk add git'
      }
    }
    stage('Clone code from Git') {
      steps {
        sh 'git clone https://github.com/linuxacademy/content-pipelines-cje-labs.git'
        sh 'pip install -r content-pipelines-cje-labs/lab3_lab4/dog_pics_downloader/requirements.txt'
      }
    }
  }
  post {
    always {
      echo "Job execution complete."
    }
    success {
      archiveArtifacts artifacts: '*.jpg'
    }
    unsuccessful {
      echo "Job execution status is failed, please check error logs"
    }
    cleanup {
      echo 'Cleaning up environment'
      sh 'rm -rf content-pipelines-cje-labs'
    }
  }
}