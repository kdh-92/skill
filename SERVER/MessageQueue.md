# MessageQueue & Event Loop

> JS 엔진의 아키텍쳐는 크게 2부분으로 나뉘어지는데 `Heap & Stack`으로 구성되어 있다.  
> Heap은 객체가 할당되어 존재하는 영역  
> Stack은 호출되는 함수가 저장되는 영역

브라우저 엔진에 Message Queue가 있는데 비동기로 처리될 콜백 함수들이 저장된다.


##### **[참고]**
[Message Queue & Event Loop](https://corock.tistory.com/464)  
[JS 엔진](https://meetup.toast.com/posts/89)  
[Blocking-NonBlocking-Synchronous-Asynchronous](https://homoefficio.github.io/2017/02/19/Blocking-NonBlocking-Synchronous-Asynchronous/)  
