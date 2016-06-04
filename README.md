# 스프링MVC 빌드 메뉴얼 #
현재 프로젝트는 gradle을 사용하여 빌드 되게 만들어져 있다.
그리고 그 밖에 숙지해야 할 사항을 아래 메뉴얼로 정리한다.

아래에도 명시 돼 있지만 해당 spring 프로젝트는 `web.xml` 설정을 사용한다. 최근 `web.xml` 사용 하지 않은 추세인듯 싶다.

## 지향하는 바 ##
- gradle을 통해 테스트 빌드 배포의 자동화를 목표(젠킨스화 통합)
- 프로젝트 버전을 아래와 같다.
	- java 1.7
	- servlet 2.5
	- web.xml 사용

## 요구 조건 ##
1. JAVA
	- 해당 프로젝트는 java 1.7 버전으로 되어있다.
	- gradle도 java 버전과 관련 있으므로 1.7 이상을 권장한다.
2. gradle
	- JAVA 빌드 툴이며 해당 프로젝트는 버전 2.4.4 버전을 기반으로 작성되었다.
	- 위 버전 이상이면 특별히 문제 될 것을 없을 듯하다.

## 명시 사항 ##
- webapp(웹 root 폴더)는 `WebContent` 디렉토리 이다.
- 코드 인코딩은 UTF-8 을 사용 한다.(이클립스 기본 인코딩은 UTF-8 이 아니니 주의해야 한다)
- 자바 버전은 1.7 서블릿 버전은 2.5 를 사용 하고 있다.
- 스프링은 4.0 을 사용 하고 있으나 낮으 버전도 가능하다.
- Commons 에 lang 라이브러리를 사용한다. 여기서 StringUtils 등을 자주 사용한다. 버전은 3.3.2 이다.
- 라이브러리 버전 은 `version` 값을 수정 해면 변경된다. 값 수정 후 다시 빌드해줘야 하는것은 잊지 말자
- 라이브러리 검색 및 버전은 [mvnrepository](http://www.mvnrepository.com/)를 통해 확인 하고 하단 텝에 `gradle`선택해 붙여 넣으면 된다.
- 스프링 컨테이너 설정을 `web.xml`, `spring-servlet.xml`이 전부이다.
- 서블릿 3.0 부터 `web.xml` 이 필요없다고 하고, 스프링 예제들도 class를 만들어 쓰는 추세이니 추후 `web.xml` 없이 구성하는 것도 좋을 듯 싶다. 
- 오라클 jdbc 드라이버(jar)를 설치하려면, 주석으로 되어있는 부분을 풀어 주고 `WebContent/WEB-INF/lib`밑에 jar 파일을 넣으면 된다. `compile` 부분은 해당 jar 파일명을 기입해야 한다.

## 빌드 방법 ##

### eclipse ###
- cmd 창을 켜고, `gradle cleanAll eclipse` 라고 쳐 주면 알아서 빌드 된다.
	- `cleanAll` : 기존에 빌드 되었던 파일을 다 초기화(삭제) 시킨다.
	- `eclipse` : eclipse 프로젝트에 맞게 빌드한다. 
- 이클립스를 켜고 해당 폴더를 import 시켜주면 정상 작동한다.

### intelliJ ###
- cmd 창을 켜고, `gradle cleanAll idea` 라고 쳐 주면 알아서 빌드 된다.
	- `cleanAll` : 기존에 빌드 되었던 파일을 다 초기화(삭제) 시킨다.
	- `idea` : intelliJ 프로젝트에 맞게 빌드한다. 
- intelliJ 켜고 해당 폴더를 열어주면 끝

## 개선 사항 ##
- 테이블 연동을 통한 VO 자동 생성 및 task 를 통해 특정 테이블만 Vo로 만들거나 테이블 수정시 task 를 통해 자동으로 Vo 수정
	- 해당 로직을 위해 [Lombok](https://projectlombok.org/)라이브러리 추가 할 예정
- TDD를 위한 세팅 추가할 예정
	- [Mockito](http://mockito.org/) 같은 테스트 라이브러리 추가
	- Mock DB 도 필요 할듯 Spring 에서 지원해주는 테스트라이브러리 확인
	- Spring Controller 테스트 예제 및 템플릿 추가



 