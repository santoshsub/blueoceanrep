pipeline {
  agent any
  stages {
    stage('Codecollection') {
      steps {
        git(url: 'https://github.com/santoshsub/simpleMavenJunit.git', changelog: true, poll: true, branch: 'master')
      }
    }

    stage('Compile') {
      steps {
        sh '''mvn clean
mvn compile'''
      }
    }

    stage('test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('reportpublish') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

  }
}