1. Собираем jenkins с docker внутри из папки jenkins_docker->Dockerfile (docker build -t jd . )

2. Права на docker.sock:
chmod 777 /var/run/docker.sock

3. Стартуем прокидывая docker.sock: 
docker run -d -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v /home/zi10ge/jen-home:/var/jenkins_home jd

