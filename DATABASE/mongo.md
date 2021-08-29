### [ 문제 발생 ]
- mac catalina 특정 버전부터 mongod로 서버를 시작시키려 할 때 에러 메세지 발생
- (NonExistentPath: Data directory /data/db not found.)
- /data/db를 찾을 수 없다는 건데 이유는 / <- root에 파일 생성을 못하게 막히면서 발생하게 됨

  
 #### `해결 방법`  
 ---
```
mkdir -p ./data/db
sudo mongod --dbpath=/Users/${username}/data/db 
```
위에 방법으로 실행 시 정상적으로 mongod 서버 실행이 되고 터미널에서 mongo로 접속이 가능해진다.
[해당 문제 해결 관련 참고 사이트](https://bongbongreview.tistory.com/73)
