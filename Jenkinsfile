pipeline {
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
        git url: 'https://github.com/shri-1307/game-of-life.git'
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
                 to: 'shree.nakkawar@gmail.com'
        }
            failure {
            mail subject: 'your project is defective',
                 body: 'your project is defective',
                 to: 'shree.nakkawar91@gmail.com'
        }
    }
}
