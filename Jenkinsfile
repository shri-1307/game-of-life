pipeline {
  agent {label 'java_8'}
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
