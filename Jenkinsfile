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

    stage('mail') {
      steps {
        mail(subject: 'New build', body: 'A new build is on the way', from: 'hi_benakcha@esi.dz', to: 'hi_benakcha@esi.dz')
      }
    }

    stage('Code Analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          bat 'gradle sonarqube'
        }

        waitForQualityGate true
      }
    }

  }
}