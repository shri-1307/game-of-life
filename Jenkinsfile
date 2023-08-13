pipeline {
  agent {label 'java_8'}
  stages {
    stage ('vcs') {
	  steps {
                 git clone "https://github.com/wakaleo/game-of-life.git"
	  }
	}
  }
	stage ('build') {
	  tools {
        jdk 'JAVA_8'
    }
	  steps {
	     mvn package
	  }
  }
}
