pipeline {
  agent {
    docker {
      image 'zi10ge/jagent:2'

    }
  }
    stages {
      stage ("Pull boxfuse source from git"){
          steps {
          git 'https://github.com/zi10ge/boxfuse-sample-java-war-hello.git'
          }
      }
      stage ("Build war"){
          steps {
          sh 'mvn package'
          }
      }
      stage ("Pull prod souce from git"){
          steps {
          git 'https://github.com/zi10ge/HW11.git'
          }
      }
      stage ("Copy WAR file to build dir"){
          steps {
          sh 'cp ./target/hello-1.0.war ./prod/hello-1.0.war'
          }
      }    
      stage ("Build app image"){
          steps {
          sh 'docker build -t zi10ge/app:last ./prod'
          }
      }  
      stage ("Push app image to dockerhub"){
          steps {
            withDockerRegistry([ credentialsId: "75bf2ec9-a2d7-4f8c-8c02-33be8335f993", url: "" ]) {
            sh 'docker push zi10ge/app'
            }
          }
      }         
    }
  }