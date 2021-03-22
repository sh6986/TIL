# Mybatis

### resultMap

### sql

### include

### choose

- 검사할 조건이 여러개일 경우 사용
- 자바의 if-else문과 유사하다
- 일치하는 조건이 없으면 <otherwise>의 SQL이 반환된다

```xml
<choose>
	<when test="조건1">SQL</when>
	<when test="조건2">SQL</when>
	<otherwise>SQL</otherwise>
</choose>
```

### collection