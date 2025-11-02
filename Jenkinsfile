node {
  stage('Checkout') { checkout scm }
  stage('Build') { sh './mvnw -B -DskipTests package' }
  stage('Test') {
    try { sh './mvnw -B test' } finally { junit 'target/surefire-reports/*.xml' }
  }
  stage('Archive') { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true }
}