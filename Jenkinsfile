pipeline {
  agent any
  environment {
    ARTIFACTOR = "${env.BUILD_NUMBER}.zip"
  }
  
  stages {
    stage("Repository") {
      steps {
          checkout scm
      }
    }
    stage("Build") {
      steps {
        // sh "zip -r ${ARTIFACTOR} ./"
      echo "este paso funcaba con el zip xD"
      sh "touch ${ARTIFACTOR}"
      //sh "docker build -t myimage:${env.BUILD_NUMBER} ."
      //sh "docker tag myimage:${env.BUILD_NUMBER} myimage:latest"
      sh "env"
      sh $"path"
      
      }
    }
    stage("Test") {
      steps {
        parallel (
          syntax: { sh "echo syntax" },
          grep: { sh "echo 'grep'" }
        )
      }
    }
  } 

  post {
    always {
      archiveArtifacts artifacts: "${ARTIFACTOR}", onlyIfSuccessful: true
      sh "rm -f ${ARTIFACTOR}"
      echo "Job has finished"
    }
  }

}
