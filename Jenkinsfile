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
    }
   stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonar-6'
    }
    steps {
        withSonarQubeEnv('Sonarqube') {
           // bat label: '', script:'ant sonar'
		bat 'ant sonar'
        }
       
    }
  }
      post {
        success {
          archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
        }
      }
      }
	 
    }

