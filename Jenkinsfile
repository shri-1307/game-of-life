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
      }
    }
stage ('build'){
	  steps {
	    sh 'mvn package'
	  }
  }

    }
}
