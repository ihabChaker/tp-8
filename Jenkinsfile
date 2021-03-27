pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        bat 'gradle archiveJar  archiveDoc'
        bat 'gradle archiveTestsResults'
      }
    }

  }
}