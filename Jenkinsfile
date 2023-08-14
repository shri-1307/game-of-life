
peline {
  agent {label 'java_8'}
  environment {
      BRANCH_NAME= 'master'
      BUILD_NUMBER= '1'
  }
  triggers { pollSCM('* * * * *') }
  tools {
        jdk 'java_8'
    }
  stages {
    stage ('vcs') {
	  steps {
        git url: 'https://github.com/wakaleo/game-of-life.git'
        echo "${BRANCH_NAME}"
        echo "${BUILD_NUMBER}"
      }
	}
    stage ('build'){
	  steps {
	     sh 'mvn package'
	  }
  }
    stage ('arctifact') {
        steps {
        archiveArtifacts artifacts: '**/surefire-reports/TEST-*.xml', followSymlinks: false
        junit testResults: '**/target/surefire-reports/TEST-*.xml'
        }
    }
  }
    post {
        success {
                 mail subject: 'your project is effective',
                 body: 'your project is effective',
                 to: 'all@qt.com'
        }
            failure {
            mail subject: 'your project is defective',
                 body: 'your project is defective',
                 to: 'all@qt.com'
        }
    }
}pipeline {
    agent any
    stages {
        stage ('vcs') {
         steps {
            git url: 'https://github.com/GitPracticeRepo/spring-petclinic.git'
         }
         }
    }
}
