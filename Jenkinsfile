node {
  stage('Checkout') {
    checkout scm
  }

  stage('Test') {
    sauce('derek_sauce_creds') {
        nodejs('11.9') {
          sh 'npm install'
          sh 'npm run test'
        }
      }
    }

  stage('Collect Results') {
    step([$class: 'SauceOnDemandTestPublisher'])
  }
}
