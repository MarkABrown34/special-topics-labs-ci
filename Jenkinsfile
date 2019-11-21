
node {
  stage('checkout sources') {
        git url: 'https://github.com/MarkABrown34/special-topics-labs-ci.git'
  }

  stage('Build') {
    withMaven (maven: 'maven3') {
              sh "mvn package"
            }
  }
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
