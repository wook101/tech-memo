-- 사용자 계정 생성 'id'@'localhost' 이면 로컬에서만 접속 가능.  
```   
CREATE USER '아이디'@'%' IDENTIFIED BY '비밀번호';   
```


-- 사용자 권한 주기.  
외부접속
```
GRANT ALL PRIVILEGES ON 데이터베이스.* TO '아이디'@'%';
```

로컬접속
```
grant all privileges on bootex.* TO 사용자@localhost identified by'사용자';
```

-- 새로고침   
```
FLUSH PRIVILEGES;
```

-- 권한 확인하기   
```
use mysql;
SELECT host, user FROM user;
```
