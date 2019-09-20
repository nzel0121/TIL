
column 명을 조회 시 VO에 camelcase 로 저장되도록 하는 설정방법
예:
```
select camel_case_column from table
```
인 경우 
application.properties 에 (또는 다른 properties에)
```
mybatis.configuration.map-underscore-to-camel-case=true
```
추가