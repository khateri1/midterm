pipeline {
  agent any
  tools { jdk "jdk17"; maven "maven3" }
  stages {
    stage("Checkout"){ steps { checkout scm } }
    stage("Build"){ steps { sh "mvn -B -DskipTests package" } }
    stage("Test"){ steps { sh "mvn -B test" } post { always { junit "target/surefire-reports/*.xml" } } }
    stage("Archive"){ steps { archiveArtifacts artifacts: "target/*.jar", fingerprint: true } }
  }
}