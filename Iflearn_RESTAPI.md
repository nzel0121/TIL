## Event 생성 API 구현 
### 입력값 제한하기
* id 같은 값은 생성되어야함 .
* 계산되어야하는 값이 입력되어서는 안됨.
> EventDto를 사용해보자


DTO -> 도메인 객체로 복사
> modelMapper를 사용해겠다. dependency 추가
```xml
<dependency>
    <groupId>org.modelmapper</groupId>
    <artifactId>modelmapper</artifactId>
    <version>2.3.0</version>
</dependency>
```


### 입력값 이외 값이 들어오면 에러를 발생
* ObjectMapper Customize
>spring.jackson.deseri..
#### TEST TODO
입력값으로 id, free등 들어오면 안되는 값이 들어오면 
BAD REQUEST로 응답


### refactoring duplicate code in testcase code 
with JunitParams
ADD dependency
```xml
<dependency>
    <groupId>pl.pragmatists</groupId>
    <artifactId>JUnitParams</artifactId>
    <version>1.1.1</version>
    <scope>test</scope>
</dependency>g
```
Sample Code
```java
@Test
@Parameters
public void testOffline(String location,boolean isOffline){
    Event event = Event.builder()
                    .location(location)
                    .build();

    event.update();

    assertThat(event.isOffline()).isEqualTo(isOffline);
}
private Object[] parametersForTestOffline(){
    return new Object[]{
            new Object[]{"강남",true},
            new Object[]{null, false}
    };
}
```
> parameters 를 사용할 때는 스트링 배열로 사용해도 되나. Type safe 하게 메소드를 이용할 수 있음 메소드를 사용하는 규약은 **parametersFor**메소드명 으로 할 수 있다.

## Spring HATEOAS introduce
* make Link
    * with String
    * with controller and method
* make resource
    * resource is data + link
* search link
    * Traverson
    * LinkDiscoverers
* Link is
    * HREF ( hypermedia reference )
    * REL ( relation )
        * self
        * profile
        * ...

## Spring HATEOAS 적용
### TEST CODE 변경
1. _link..self 가 넘어오는지 확인
2. _link.query-events - 이벤트목록을 가져오는 링크
3. _link.update-event - 이벤트를 변경하는 링크


## Spring REST Doc 소개
Spring Boot 에서는 @Annotation 으로 추가가능 
> @AutoConfigureRestDocs

### Rest Docs 코딩
* andDo(document("",links())) <-- 같은형태로..
* snippets
    * links()
    * requestParameters() + parameterWithName()
    * pathParameters() + parametersWithName()
    * requestParts() + pathWithName()
    * requestFelds() + fieldWithPath()
    * responseField()
    * ...

### 문서생성
* mvn package
    * test
    * prepare-package :: process-asciidoc
    * prepare-package :: copy-resources
* 문서확인
    * /docs/index.html

### Constraint

### RestDocMocMvc 커스터마이징
* RestDocsMockMvcConfigurationCustomizer 를 구현해서 빈등록
* @TestConfiguration

### TEST TODO
* API 문서만들기
    * 요청문서화
    * 응답문서화
    * 링크문서화
    * profile 링크 추가

### postgres 
docker pull postgres
docker run --name rest -p 5432:5432 -e POSTGRES_PASSWORD=pass -d postres
docker exec -i -t rest bash
su - postgres
psql -d postgres -U postgres
psql -d postgres -U postgres -W
Password :
database 찾는명령 \l

docker exec -i -t rest bash

