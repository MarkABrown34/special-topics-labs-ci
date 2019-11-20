
node {
  stage('checkout sources') {
        // You should change this to be the appropriate thing
        git url: 'https://github.com/MarkABrown34/special-topics-labs-ci.git'
  }

  stage('Build') {
    // you should build this repo with a maven build step here
    withMaven (maven: 'maven3') {
              sh "mvn package"
            }
  }
  // you should add a test report here
  node {
      try {
          stage('Test') {
              withMaven (maven: 'maven3'){
              sh "mvn test"
              }
          }
      } finally {
          junit 'target/surefire-reports/**/*.xml'
      }
  }
}
