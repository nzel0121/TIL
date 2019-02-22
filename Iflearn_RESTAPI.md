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
</dependency>
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