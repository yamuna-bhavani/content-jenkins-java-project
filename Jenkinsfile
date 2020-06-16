pipeline {
  agent none

  environment {
    MAJOR_VERSION = 1
  }

  stages {
    
    stage('Unit Tests') {
      agent any
      steps {
        bat 'ant -f test.xml -v'
        junit 'reports/result.xml'
      }
    }
    stage('build') {
      agent any
      steps {
        bat 'ant -f build.xml -v'
      }
   
      post {
        success {
          archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
        }
      }
      }
	 
    }
}
