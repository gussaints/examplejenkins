pipeline {
  agent any
  stages {
    stage('clone repository') {
      steps {
        sh '''java -version
mvn --version
git --version'''
      }
    }

    stage('Deploy billing App') {
      steps {
        withCredentials(bindings: [
                      string(credentialsId: 'k8s-jnkns-srvr-account', variable: 'api_token')
                      ]) {
            sh 'kubectl --token $api_token --server https://192.168.49.2:8443 --insecure-skip-tls-verify=true apply -f deploy-back-jnkns.yaml '
          }

        }
      }

    }
  }
