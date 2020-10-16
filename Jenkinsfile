pipeline {
  agent {
    docker {
      image 'zi10ge/jagent:5'

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
      stage ("Pull production app souce from git"){
          steps {
          git 'https://github.com/zi10ge/HW11.git'
          }
      }
      stage ("Copy WAR file to build dir"){
          steps {
          sh 'cp ./target/hello-1.0.war ./app/hello-1.0.war'
          }
      }    
      stage ("Build app image"){
          steps {
          sh 'docker build -t zi10ge/app:latest ./app'
          }
      }  
      stage ("Push app image to dockerhub"){
          steps {
            withDockerRegistry([ credentialsId: "75bf2ec9-a2d7-4f8c-8c02-33be8335f993", url: "" ]) {
            sh 'docker push zi10ge/app'
            }
          }
      }
      stage ("Test app get page"){
          steps {
          sh 'docker run --rm --name myapp -d -p 80:8080 zi10ge/app:latest'
          sh 'sleep 10'
          sh 'wget --quiet -O - http://84.201.161.47:80/hello-1.0'
          sh 'docker stop myapp'
          }
      }        
    }
  }