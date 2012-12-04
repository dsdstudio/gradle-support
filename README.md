## gradle-support

### common-support.gradle
공통적으로 사용하는 설정들을 모아놨다. 

- java compile encoding default utf-8
- dependency repository non-caching (snapshot repo에서 작업할경우를 대비)


### eclipse-support.gradle

- class / testClasses 폴더 분리 (runtime resource / test resource 가 섞여서 생기는 문제 발생소지를 없앤다.)


  gradle eclipse

### initialize-support.gradle 

- source / test / resource 디렉토리를 초기화하는 스크립트 모음 

  gradle initialize

