pipeline {
  agent {
    docker {
      image 'zi10ge/jagent'
      args '-v /var/run/docker.sock:/var/run/docker.sock -u root:docker'
    }
  }
    stages {
      stage ("test1"){
          steps {
          sh 'echo test'
          }
      }
    }
  }