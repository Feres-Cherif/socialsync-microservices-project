pipeline {
  agent any 
  environment {
    KUBECONFIG = '/var/jenkins_home/.kube/config'
  }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Verify tools') {
      steps {
        sh 'docker --version'
        sh 'kubectl version --client'
        sh 'kind version'
      }
    }
    stage('Validate manifests') {
      steps { sh 'kubectl kustomize k8s/ > /dev/null && echo "Manifestes Kubernetes valides"' }
    }
    stage('Cluster status') {
      steps { sh 'kubectl -n socialsync get pods' }
    }
  }
}
