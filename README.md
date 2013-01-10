## gradle-support

DRY(Do not Repeat YourSelf!) 개인적으로 사용하는 gradle 설정들을 종류별로 모아봤습니다. 매번 파일로 추가하기보다는 인터넷이 되는 환경이라면 `apply from:url` 의 형태로 간단히 추가해서 자주쓰는설정들의 중복을 없앱니다. 

### common-support.gradle
일반적인 Project에서 공통적으로 사용하는 설정. 

- java compile encoding default utf-8
- dependency repository non-caching (snapshot repo에서 작업할경우를 대비)

#### 사용 방법 

    apply from: 'https://raw.github.com/dsdstudio/gradle-support/master/common-support.gradle'


### eclipse-support.gradle

> class / testClasses 폴더 분리 (runtime resource / test resource 가 섞여서 생기는 문제 발생소지를 없앤다.) (예) class folder 와 testclass 디렉토리가 같을때 emma test 시 byte code에 emma관련 import package가 같이 딸려들어간다던지..   

    $ gradle eclipse

#### 사용 방법 

    apply from: 'https://raw.github.com/dsdstudio/gradle-support/master/eclipse-support.gradle'


### initialize-support.gradle 

> source / test / resource 디렉토리를 초기화하는 스크립트 모음 (프로젝트 시작시 bootstrap용으로 사용된다)

	$ gradle initialize

#### 사용 방법 

    apply from: 'https://raw.github.com/dsdstudio/gradle-support/master/initialize-support.gradle'

### mvn-support.gradle 

> mvn localrepository, remoterepository에 배포할때 사용한다. 

#### Properties 정리 

- username : nexusloginid
- userpassword : nexuspassword
- nexussnapshotrepository : your nexus snapshot repository
- nexusreleaserepository : your nexus snapshot repository

#### 사용방법 

build.gradle 

	apply plugin: 'maven'
	apply from: 'https://raw.github.com/dsdstudio/gradle-support/master/mvn-support.gradle'

##### local repository에 배포 

	$ gradle install

##### remote repository에 배포 

	$ gradle -Pusername=nexususername -Puserpassword=nexususerpassword -Pnexussnapshotrepository=http://custom_nexus_hostname:port/snapshots/ -Pnexusreleaserepository=http://custom_nexus_hostname:port/releases

설정이 너무 길다 싶으면 gradle.properties 에 해당 설정을 빼면 된다. 
