node {
  stage('Checkout') {
    checkout scm
  }

  stage('Test') {
    sauce('saucelabs') {
      sauceconnect(useGeneratedTunnelIdentifier: true, verboseLogging: true) {
        nodejs('11.9') {
          sh 'npm install'
          sh 'npm run test'
        }
      }
    }
  }

  stage('Collect Results') {
    step([$class: 'SauceOnDemandTestPublisher'])
  }
}
