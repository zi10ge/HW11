pipeline {
  agent {
    docker {
      image 'zi10ge/jagent:3'

    }
  }
    stages {
      stage ("Copy source from git"){
          steps {
          git 'https://github.com/zi10ge/boxfuse-sample-java-war-hello.git'
          }
      }
      stage ("Build war"){
          steps {
          sh 'mvn package'
          }
      }
    }
  }