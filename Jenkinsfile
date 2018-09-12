#!groovy

chuckNorris()

pipeline {
  agent any
  stages {
    stage('Build MTA') {
      steps {
        sh "/tools/buildMTA.sh ${params.hdiContainerName} ${params.userId}"
        archiveArtifacts artifacts: "xsahaa-master-${params.userId}.mtar"
      }
    }
    stage('Deploy to CF') {
      steps {
        sh "/tools/deployToCF.sh ${params.userId}"
      }
    }
  }
}
