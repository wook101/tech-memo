data.sql 파일을 만들어서 초기 데이터를 로드한다.   
'''   
INSERT INTO country (name) VALUES ('India');   
INSERT INTO country (name) VALUES ('Brazil');   
INSERT INTO country (name) VALUES ('USA');   
INSERT INTO country (name) VALUES ('Italy');
'''
   
[주의 사항]   
Hibernate가 초기화되기 전에 data.sql이 먼저 실행되기 때문에   
application.yml에 spring.jpa.defer-datasource-initialization: true 옵션을 추가한다.   


schema.sql 파일   
때로는 기본 스키마 생성 메커니즘에 의존하고 싶지 않습니다. 이러한 경우 사용자 지정 schema.sql 파일을 만들 수 있습니다 .   
'''
CREATE TABLE country (
    id   INTEGER      NOT NULL AUTO_INCREMENT,
    name VARCHAR(128) NOT NULL,
    PRIMARY KEY (id)
);
'''
Spring은이 파일을 선택하여 스키마 생성에 사용합니다.   
   
충돌을 피하기 위해 자동 스키마 생성을 해제하는 것도 중요합니다.   
   
spring.jpa.hibernate.ddl-auto=none   
