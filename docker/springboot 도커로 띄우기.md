1. 스프링 부트 프로젝트 생성   
2. docker설치하기   
3. 프로젝트 루트에 DockerFile작성하기  
   
DockerFile      
```
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

4. maven으로 빌드하기   
./mvnw package   
   
5. docker 이미지로 만들기   
docker buile -t [(생성할이미지명)group/artifact] .   
   
6. docker images 명령어로 생성된 이미지 확인   
   
7. docker run -d -p 8081:8080 book/springboot-docker   
-d : 백그라운드 모드   
-p : 호스트와 컨테이너의 포트를 연결 (포워딩)   
브라우저 요청 > 8081(컨테이너) > 8080(springboot)   
   
8. docekr ps 구동확인
