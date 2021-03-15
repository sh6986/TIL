# Spring, Spring Boot

# 1. Spring 이란?

소규모 어플리케이션 또는 기업용 어플리케이션을 자바로 개발하는데 있어 유용하고 편리한 기능을 제공하는 프레임워크

## 1.1 Spring의 진짜 핵심

- 스프링은 자바 언어 기반의 프레임워크
- 자바 언어의 가장 큰 특징 - **객체지향언어**
- 스프링은 객체지향 언어가 가진 강력한 특징을 살려내는 프레임워크

스프링은 **좋은 객체지향** 애플리케이션을 개발할 수 있게 도와주는 프레임워크

## 1.2 좋은 객체지향 프로그래밍?

- 추상화
- 캡슐화
- 상속
- **다형성**

### 다형성의 실세계 비유

- **역할**과 **구현**으로 세상을 구분
- 예) 운전자 - 자동차

![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled.png)

클라이언트는 **대상의 역할(인터페이스)**만 알면 된다.

클라이언트는 **내부 구조를 몰라도** 된다. 

클라이언트는 **내부구조가 변경**되어도 영향을 받지 않는다.

클라이언트는 **구현대상 자체를 변경**해도 영향을 받지 않는다.

### 역할과 구현을 분리

- 자바 언어의 다형성을 활용

    **역할 = 인터페이스**

    **구현 = 인터페이스를 구현한 클래스, 구현 객체**

- 장점
    - 유연하고 변경이 용이
    - 확장 가능한 설계
    - 클라이언트에 영향을 주지 않는 변경 가능

### 스프링과 객체지향

- 스프링은 **다형성**을 극대화해서 이용할 수 있게 도와준다.
- 스프링에서 이야기하는 제어의 역전(IoC), 의존관계 주입(DI)은 **다형성**을 활용해서 역할과 구현을 편리하게 다룰 수 있도록 지원
- 스프링을 사용하면 마치 레고블럭 조립하듯이 공연무대 배우를 선택하듯이 **구현을 편리하게 변경가능**

## 1.3 Spring의 단점을 보완한 Spring Boot

- 스프링을 편리하게 사용할 수 있도록 지원
- Tomcat 같은 **웹 서버를 내장**해서 별도의 웹 서버를 설치하지 않아도 됨
- starter를 통한 dependency 자동화
- jar file을 이용해 자바 옵션만으로 손쉽게 배포 가능

## 1.4 Spring의 핵심 : 관심사의 분리 - AOP(Aspect Oriented Programming)

- 애플리케이션을 하나의 공연이라고 생각하고 각각의 인터페이스를 배역이라 생각할 때 실제 배역에 맞는 배우를 선택하는 것은 누가 하는가?
- 배역은 배우들이 정하는 것이 아니다.
- 배우는 본인의 역할인 배역을 수행하는 것에만 집중해야 한다.
- 공연을 구성하고, 담당배우를 섭외하고, 역할에 맞는 배우를 지정하는 책임을 담당하는 별도의 **'공연 기획자'**를 만들고 배우와 공연 기획자의 책임을 확실히 분리해야 한다.
- **어떤 로직을 핵심적인 관점, 부가적인 관점으로 나누어서 보는 것**
- **AOP** **- 핵심 기능과 공통 기능을 분리시켜놓고, 공통 기능을 필요로 하는 핵심기능들에서 사용하는 방식**

## 1.5 Spring의 핵심 : IoC, DI, 컨테이너

### 제어의 역전 - IoC (Inversion Of Control)

- 기존 프로그램은 클라이언트 구현 객체가 스스로 필요한 서버구현객체를 생성하고, 연결하고, 실행했다. 한마디로 구현 객체가 프로그램의 제어흐름을 스스로 조종했다.
- 반면에 AppConfig가 등장한 이후에 구현객체는 자신의 로직을 실행하는 역할만 담당한다. 프로그램의 제어 흐름은 이제 AppConfig가 가져간다. **구현 객체는 자신의 로직을 실행할 뿐**이다.
- 프로그램에 대한 제어 흐름에 대한 권한은 AppConfig가 가지고 있다. 이렇듯 **프로그램의 제어 흐름을 직접 제어하는것이 아니라 외부에서 관리하는 것을 제어의 역전(IoC)**이라 한다.

### 의존관계 주입 - DI (Dependency Injection)

- 의존성을 주입시켜준다. 객체를 직접 생성하지 않고 **외부에서 생성한 후 주입**을 시켜준다.
- 장점 - 코드의 수정이 용이하다.
- 객체를 직접 생성하는 방법

    ![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%201.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%201.png)

- 외부에서 생성된 객체를 setter() 나 생성자를 통해 사용하는 방법

    ![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%202.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%202.png)

- 스프링은 다른 객체들이 사용하고, 다른 서비스를 위해 사용할 수 있는 클래스를 컨테이너 형태로 이 기능을 제공

    ![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%203.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%203.png)

## 1.6 스프링 컨테이너

- **객체를 생성하고 관리하면서 의존관계를 연결해 주는 것**을 스프링 컨테이너라고 한다.
- 기존에는 개발자가 직접 객체를 생성하고 DI를 했지만, 이제부터는 스프링 컨테이너를 통해서 사용
- 스프링 컨테이너는 @Configuration이 붙은 AppConfig를 설정정보로 사용. 여기서 @Bean이라 적힌 메서드를 모두 호출해서 반환된 객체를 스프링 컨테이너에 등록한다. 이렇게 스프링 컨테이너에 등록된 객체를 스프링 빈이라 한다.
- 스프링 빈은 @Bean이 붙은 메서드의 명을  스프링 빈의 이름으로 사용한다.
- 기존에는 개발자가 직접 자바코드로 모든것을 했다면 이제부터는 스프링 컨테이너에 객체를 스프링 빈으로 등록하고, 스프링 컨테이너에서 스프링 빈을 찾아서 사용하도록 변경되었다.

### 싱글톤 패턴

생성자가 여러차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다.

![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%204.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%204.png)

### 싱글톤 패턴을 사용하는 이유

요청이 엄청나게 많은 트래픽 사이트에서 요청을 할 때 마다 새로운 객체를 생성하게 되면 **메모리 낭비가 심하기 때문이다.**

### 스프링의 싱글톤 패턴

- 스프링 컨테이너는 싱글톤 패턴을 적용하지 않아도 객체 인스턴스를 싱글톤으로 관리한다. 이러한 기능 덕분에 싱글톤 패턴의  모든 단점을 해결하고 객체를 싱글톤으로 유지할 수 있다.
- 스프링에서 컨테이너 내 특정 클래스에 대해 @Bean이 정의되면, 스프링 컨테이너는  그 클래스에 대해 단 하나의 인스턴스를 만든다.

---

# 2. build(maven, gradle)

## 2.1 빌드란

소스코드를 실행할 수 있는 소프트웨어 형태로 변환하는 과정

→ java 코드와 프로젝트 내에 필요한 각종 xml, properties, jar 파일들을 JVM이나 WAS가 인식할 수 있도록 패키징해주는 과정

## 2.2 빌드 툴

- 프로젝트 생성, 테스트 빌드, 배포 등 전체적인 라이프사이클을 관리하기 위한 전용 프로그램
- 엔터프라이즈 개발시 일어나는 빈번한 라이브러리 추가 및 버전 동기화의 어려움을 해소
- 코드 컴파일, 컴포넌트 패키징, 개발 테스트 실행, 버전관리 도구 통합, 문서생성, 배포기능 포함
- maven, gradle 등이 있다.

## 2.3 Maven 이란?

- 자바용 프로젝트  관리 도구
- 필요한 라이브러리를 특정문서(pom.xml)에 정의해 놓으면 내가 사용할 라이브러리 뿐만 아니라 해당 라이브러리가 작동하는데에 필요한 다른 라이브러리들까지 관리하여 네트워크를 통해서 자동으로 다운받아준다.
- 간단한 설정을 통한 배포관리가 가능하다.

## 2.4 Maven 의 단점을 보완한 Gradle

- Gradle이 시기적으로 늦게 나온만큼 사용성, 성능 등 비교적 뛰어난 스펙을 가지고 있다.
- Gradle의 빌드 스크립트는 groovy 라는 언어로 작성해야 하므로 Maven 의 xml 에 비하면 친숙하지 않지만 **확장성이 뛰어나다**
- Maven 은 프로젝트가 커질수록 빌드 스크립트의 내용이 길어지고 가독성이 떨어지는 반면, Gradle은 훨씬 적은양의 스크립트로 **짧고 간결하게 작성할 수 있다.**
- 캐시 사용으로 Maven 보다 **빌드 속도가 빠르다**

## 2.5 JAR, WAR

- java의 jar 툴을 이용해 생성된 압축파일
- 어플리케이션을 쉽게 배포하고 동작시킬 수 있도록 관련 파일(리소스, 속성파일)들을 패키징 해 주는 것

### JAR(Java ARchive)

- 원하는 구조로 구성 가능
- 실행조건 : java만 있으면 실행가능

### WAR(Web application ARchive)

- web application을 지원하기 위한 압축방식
- 단독으로 실행 불가하며 서버 컨테이너(WAS)에 의해 실행되어야 하므로 배포스크립터(web.xml)이 포함됨
- 내부 조건 : web-inf 폴더에 포함된 web.xml 필요
- 실행 조건 : java ee web profile 호환 응용 프로그램 서버 필요

---

# 3. 개발을 위한 설정

## 3.1 설정 - Mybatis

### Mybatis란?

객체지향 언어인 자바의 관계형 데이터베이스 프로그래밍을 보다 쉽게 도와주는 프레임워크

### Mybatis 특징

- **쉬운 접근성과 코드의 간결함**

    JDBC 사용시 많은 코드를 반복하여 사용하지만 Mybatis는 이러한 코드를 상당히 줄여줄 수 있어 개발 생산성 향상에 크게 기여

- **SQL문과 프로그래밍 코드의 분리**

    JDBC방식은 개발자가 SQL문을 처리하기 위해 별도의 파일을 작성하는 등의 번거로운 작업을 필요로 한다. 반면에 Mybatis는 XML또는 어노테이션을 사용해 별도로 처리하는 작업이 가능

- **동적 SQL을 이용한 제어**

    내부적으로 제어문이나 루프 등의 처리기능을 가지고 있다. 이를통해 SQL문의 결과와 관련된 처리를 java코드에서 분리하여 작성 가능

### Mybatis 사용이유

- JDBC - Java에서 DB와 연동하고 쓰기 위해 사용하는 API
- JDBC만 사용해서 DB 쿼리문을 작성하면 Java 소스와 쿼리소스가 겹치게 되고 관리가 어려워진다.
- Mybatis는 SQL 쿼리문을 xml 형식의 파일로 분리시켜 저장관리할 수 있고 java소스에서 xml태그의 id만 호출하며 개발의 편리함을 제공한다.
- Mybatis는 xml형식의 쿼리 파일을 저장 및 호출하는 역할을 내부적으로 처리하는 것이다.
- Mybatis를 사용하지 않을 때 코드

    ```java
    public Entity selectFAQList(UserConnection conn, Entity param) throws SQLException {
        UserStatement stmt = null;
        ResultSet rslt = null;
        StringBuffer sql = new StringBuffer();
        sql.append("\n SELECT *");
        sql.append("\n FROM");
        sql.append("\n TABLE1");
        stmt = conn.prepareStatement(sql.toString());
        rslt = stmt.executeQuery();
        Entity _DATA = new Entity();
        _DATA.put("_DATA", EntityUtil.ResultSetToClobList(rslt));
        return _DATA;
    ```

    이러한 방식은 쿼리가 수정될 때 마다 .java에  들어가 .append() 메소드를 추가하고 저장해 **유지보수가 힘들고 sql query 구문의 분리가 어려워지고 복잡**해진다.

    또한 쿼리양이 많아질수록 .java에는 자바코드 뿐만 아니라 쿼리코드로 인해 **양이 방대해지는 문제가 발생**한다.

- Mybatis를 사용할 때 코드

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
      <ENTITY id="table.getTable1List" type="SQL" return="List">
        <![CDATA[
            SELECT *
                FROM
                TABLE1
        ]]>
        <PARAMS>    
        </PARAMS>
      </ENTITY>
    ```

    xml로 빼내서 쿼리문을 작성하면 내부적 처리는 Mybatis에서 모두 처리해준다.

### Mybatis 설정

- **SqlSessionFactory**

    Mysql서버와 Mybatis를 연결해주는 객체

    SqlSessionFactoryBean 사용해서 객체 생성

- **SqlSessionTemplate**

    핵심적인 역할을 하는 클래스로서 SQL실행이나 트랜잭션 관리를 한다.

```java
@Bean
public SqlSessionFactory sqlSessionFactory(DataSource dataSource) throws Exception {

		// sqlSessionFactory 객체 생성
    SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
		// sqlSessionFactory 객체에 DataSource 객체 넣어준다.
    sqlSessionFactoryBean.setDataSource(dataSource);

		// 리소스 경로 객체
    PathMatchingResourcePatternResolver resolver = new PathMatchingResourcePatternResolver();
		// 패턴으로 표현되는 범위로부터 클래스들의 리소스 정보를 읽어들여서 
		// sqlSessionFactoryBean 객체에 mapper 경로를 넣어준다.
    sqlSessionFactoryBean.setMapperLocations(resolver.getResources("classpath:mapper/**/*.xml"));

    return sqlSessionFactoryBean.getObject();
}

@Bean
public SqlSessionTemplate sqlSessionTemplate(SqlSessionFactory sqlSessionFactory) {

    SqlSessionTemplate sqlSessionTemplate = new SqlSessionTemplate(sqlSessionFactory);
    sqlSessionTemplate.getConfiguration().setMapUnderscoreToCamelCase(true);

    return sqlSessionTemplate;
}
```

---

## 3.2 설정 - Filter, Interceptor, AOP

### Filter

- Dispatcher Servlet 영역에 들어가기 전 Front Controller 앞 범위에서 수행된다.
- 또한, Controller 이후 자원처리가 끝난 후 응답처리에 대해서도 변경, 조작을 수행할 수 있다.

### Filter 설정

- init() - 필터 인스턴스 초기화
- dofilter() - 실제 처리 로직
- destroy() - 필터 인스턴스 종료

```java
public class CommonFilter implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        filterChain.doFilter(servletRequest, servletResponse);
    }

    @Override
    public void destroy() {
    }
}
```

### Interceptor

- 스프링의 DispatcherServlet이 Controller를 호출하기 전, 후에 끼어들기  때문에 스프링 컨텍스트 내부에서 Controller에 관한 요청과 응답에 관여한다.
- 스프링의 모든 @Bean에 접근이 가능하다.

### Interceptor 설정

- preHandler() - Controller 실행 전
- postHandler() - Controller 실행 후 view Rendering 실행 전
- afterCompletion() - view Rendering 이후

```java
public class CommonInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {

        HttpSession session = request.getSession();
        MemberDTO memberDTO = (MemberDTO) session.getAttribute("memberInfo");

        if (null == memberDTO) {

            StringBuffer redirectUrl = new StringBuffer();
            redirectUrl.append(request.getScheme()).append("://")
                       .append(request.getServerName()).append(":")
                       .append(request.getServerPort()).append("/")
                       .append(request.getContextPath())
                       .append("view/member/login");

            response.sendRedirect(redirectUrl.toString());
            return false;
        }
        return true;
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
    }
}
```

### AOP(Aspect Oriented Programing)

- Controller 처리 이후 주로 비즈니스 로직에서 실행된다.
- Filter와 Interceptor와 달리 메소드 전후 지점에서 자유롭게 설정이 가능
- 주소, 파라미터, 어노테이션 등 다양한 방법으로 대상을 지정할 수 있다.

### AOP 주요 개념

- **Aspect** : 흩어진 관심사를 모듈화 한 것. 주로 부가기능을 모듈화함
- **Target** : Aspect를 적용하는 곳 (클래서, 메서드..)
- **Advice** : 실질적으로 어떤일을 해야할 지에 대한 것, 실질적인 부가기능을 담은 구현체
- **JoinPoint** : Advice가 적용될 위치, 끼어들 수 있는 지점. 메서드 진입 지점, 생성자 호출 시점, 필드에서 값을 꺼내올 때 등 다양한 시점에 적용 가능
- **PointCut** : JointPoint의 상세한 스펙을 정의한 것. 'A란 메서드의 진입 시점에 호출할 것'과 같이 더욱 구체적으로 Advice가 실행될 지점을 정할 수 있음

### AOP 설정

```java
@Component
@Aspect
public class CommonAOP {

    private static final Loggerlogger= LoggerFactory.getLogger(CommonAOP.class);

    @Around("execution(* com.example.bootsample.biz.member.controller.MemberController.*(..)) || "
                + "execution(* com.example.bootsample.biz.file.controller.FileController.*(..))")
    public Object logging(ProceedingJoinPoint joinPoint) throws Throwable{

        HttpServletRequest request = ((ServletRequestAttributes) RequestContextHolder.currentRequestAttributes()).getRequest();
        Object result = joinPoint.proceed();
logger.info("Request URL : " + request.getRequestURL());

        return result;
    }
}
```

### filter, Interceptor, AOP 차이점

![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%205.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%205.png)

- 중간에 가로채서 사전처리나 사후처리를 하는 점은 같다.
- 차이점은 **시점이 다르다는 것**
- filter는 스프링 밖의 영역, interceptor와 aop는 스프링 영역에서 이루어진다.
- **순서 : filter → interceptor → aop**
- 시점에 따라 **용도**가 달라진다.

    filter - 인코딩 변환처리, xss 방어개발 시 사용

    interceptor - 로그인 처리

    aop - 로깅, 트랜잭션 처리

---

## 3.3 설정 - 로깅

### 로깅의 시작

- 태초에 스프링은 **JCL(Jakarta Commons Logging)**을 사용해서 로깅을 구현
- JCL을 사용하면 기본적인 인터페이스인 Log와 Log객체생성을 담당하는 LogFactory만 구현하면 얼마든지 다른 로깅구현체로 교체가능
- JCL이 구현체를 선택하는 시점이 런타임이라 클래스 로더에 의존적이다.
- JCL 문제점 - **가바지 컬렉션이 제대로 작동하지 않는 치명적인 문제** 발생
- 문제 해결을 위해 클래스로더 대신 컴파일시점에 구현체를 선택하도록 변경됨. 이때 도입되는것이 **SLF4J**이다.
- SLF4J에서는 컴파일 시점에 로깅구현체를 결정한다. 스프링부트에서는 **Logback**이 기본으로 선택되어 있다.

### SLF4J(Simple Logging Facade For Java)

- 스프링이 기존에 사용하던 로그 라이브러리 JCL대신 새로운 라이브러리 Logback을 사용하기 위해서는 SLF4J 가 필요하다.
- SLF4J는 일명 **Facade** 패턴으로 이를 사용하면 구현체의 종류와 상관없이 **일관된 로깅 코드**를 작성할 수 있으며 구현체를 변경할 경우에도 최소한의 수정으로 교체가 가능하다.

### **Logback**

- 기존 로그를 관리하기 위한 구현체로써 log4j 가 사용되었다.
- 그러나 보다 안정성이 높고 편리하게 로그를 관리하기 위해 SLF4j와 그 구현체로써 Logback이 고안되었다.

### Logback의 특징

- **Level**

    로그에 레벨 설정 가능. 로그마다 레벨을 설정해두고 설정파일에서 출력 로그 레벨을 설정하여 원하는 단계의 로그만 출력 가능

- **Appender**

    출력 방법 선택가능. 출력 위치(콘솔, 파일 등)나 출력 내용(날짜/시간, 레벨 등)에 대한 패턴을 설정 가능

- **Logger**

    로그마다 다른 설정내용을 쉽게 적용 가능

    위의 주요설정을 포함한 다양한 설정항목을 가지고 있는 객체(Logger)에 이름을 부여하여 필요한 상황에 맞게 적절한 Logger를 호출하여 사용 가능

### 로그레벨 순서 및 사용방법

TRACE < DEBUG < INFO < WARN < ERROR

1. **ERROR** : 요청을 처리하는 중 오류가 발생한 경우 표시
2. **WARN** : 처리 가능한 문제, 향후 시스템 에러의 원인이 될 수 있는 경고성 메시지를 나타낸다.
3. **INFO** : 상태변경과 같은 정보성 로그를 표시한다.
4. **DEBUG** : 프로그램을 디버깅 하기 위한 정보를 표시한다.
5. **TRACE** : 추적 레벨은 Debug 보다 훨씬 상세한  정보를 나타낸다.

### Logback 설정

Logback을 사용하기 위해서는 다음과 같은 tag들로 구성되어있다.

- Logger : **로그의 주체**. 로그의 메시지 전달. 특정 패키지 안의 특정레벨이상인 것에 대해 출력
- Appender : **어디에** 출력할지에 대해 기술(console / file / DB appender)
- Encode : **어떻게** 출력할지에 대해 기술

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration>
<configuration>
    <!-- 콘솔에 로그를 남긴다. -->
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <filter class="com.example.bootsample.common.filter.LogbackFilter"/>
        <encoder>
            <!-- %d:로그기록시간, %thread:현재 Thread 이름, %-3level:로그레벨 -3은 출력의 고정폭(3글자)
                 %logger{5}:축약된 logger name 5는 최대 자릿수, %msg:로그메시지, %n:줄바꿈 -->
            <pattern>%d{yyyyMMdd HH:mm:ss.SSS} [%thread] %-3level %logger{5} - %msg %n</pattern>
        </encoder>
    </appender>

    <root level="INFO">
        <appender-ref ref="STDOUT" />
    </root>
</configuration>
```

### Log4jdbc

스프링에서 SQL문을 실행한 로그를 효과적이고 직관적으로 볼 수 있도록 해주는 라이브러리

- Log4jdbc 사용하지 않을 때

    ![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%206.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%206.png)

- Log4jdbc 사용할 때

    ![Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%207.png](Spring,%20Spring%20Boot%20f7152638980b45c1a246837f809efa92/Untitled%207.png)

### Log4jdbc 설정

```xml
<!-- log4jdbc 옵션 설정 -->
<logger name="jdbc" level="OFF" />
<!-- 커넥션 open close 이벤트를 로그로 남긴다. -->
<logger name="jdbc.connection" level="OFF" />
<!-- SQL문만을 로그로 남기며, PreparedStatement일 경우 관련된 argument 값으로 대체된 SQL문이 보여진다. -->
<logger name="jdbc.sqlonly" level="OFF" />
<!-- SQL문과 해당 SQL을 실행시키는데 수행된 시간 정보(milliseconds)를 포함한다. -->
<logger name="jdbc.sqltiming" level="DEBUG" />
<!--
    ResultSet을 제외한 모든 JDBC 호출 정보를 로그로 남긴다.
    많은 양의 로그가 생성되므로 특별히 JDBC 문제를 추적해야 할 필요가 있는 경우를 제외하고는 사용을 권장하지 않는다.
-->
<logger name="jdbc.audit" level="OFF" />
<!-- ResultSet을 포함한 모든 JDBC 호출 정보를 로그로 남기므로 매우 방대한 양의 로그가 생성된다. -->
<logger name="jdbc.resultset" level="OFF" />
```

---

## 3.4 설정 - ExceptionHandler

- Exception이 발생하면 throw를 통해서 비즈니스 로직을 중단시키는 것에 그치지 않고 클라이언트에 어떤 문제가 있었는지 전달할 필요가 있다.
- Spring에서는 이런 필요성을 충족하기 위해 @ExceptionHandler 어노테이션을 제공한다.

### ExceptionHandler 설정

```java
@ControllerAdvice
public class CommonExceptionHandler {

    private static final Loggerlogger= LoggerFactory.getLogger(CommonExceptionHandler.class);

    @ExceptionHandler(Exception.class)
    public ResultDTO handleException(Exception ex) {
        //TODO : res return
logger.info("========== Exception ==========");
logger.error("Exception error: ", ex);

        return new ResultDTO(MessageConstants.ResponseEnum.SERVER_ERROR);
    }
}
```

---

# 4. API

## 4.1 REST API

### REST(REpresentational State Transfer)

자원의 표현(HTTP URI)을 가지고 상태 전달(HTTP Method)의 의미

### REST 제약조건

1. **Uniform interface(유니폼 인터페이스)**

    HTTP 표준을 따른다면 어떤 플랫폼이든 사용 가능

2. **Stateless(무상태성)**

    HTTP 표준을 그대로 사용하기 때문에 무상태성을 갖는다.

3. **Cacheable(캐시가능)**

    HTTP 표준을 그대로 사용하기 때문에 캐싱가능

4. **Client - Server 구조**

    자원을 가진 쪽이 Server. 자원을 요청하는쪽이 Client 로서 서로에게 독립적으로 구현할 수 있다.

    클라이언트는 단지 자원의 URI만 알면 된다.

5. **계층형 구조**

    클라이언트 서버가 분리되어 있어 중간에 프록시서버, 암호화 계층 등 중간매체를 사용할 수 있다.

제약조건을 모두 만족시 "RESTful" 하다 표현

### REST API

REST 기반으로 서비스 API를 구현한 것

### REST API 설계기본규칙

1. URI는 정보의 자원을 표현해야 한다.

    → 동사보다는 **명사**를 사용한다.

2. 자원에 대한 행위는 **HTTP Method**(GET, POST, PUT, DELETE 등)으로 표현한다.

    → HTTP Method나 동사표현이 URI에 들어가면 안된다.

### 그외 설계규칙

- (/)는 **계층관계**를 나타내는데 사용한다.
- 대문자보다는 **소문자**를 사용한다.
- 언더바(_)대신 **하이픈(-)**을 사용한다.
- URI 마지막 문자로 (/)를 포함하지 않는다.
- 파일 확장자는 URI에 포함시키지 않는다.

### REST API 구현

- 파일 업로드 - **POST**
- 파일 수정 - **PUT**
- 파일 리스트, 파일 단건조회 - **GET**

```java
@RestController
@RequestMapping(value = "/file")
public class FileController {

    // 파일 업로드
    @RequestMapping(value = "/upload", method = RequestMethod.POST)
    public ResultDTO upload(@RequestParam("file") MultipartFile inputFile, @RequestParam("fileDesc") String fileDesc, HttpServletRequest request) throws IOException {
        return new ResultDTO();
    }

    // 파일 수정
    @RequestMapping(value = "/{fileNo}", method = RequestMethod.PUT)
    public ResultDTO modify(@RequestBody FileDTO fileDTO, @PathVariable final int fileNo) throws Exception{
        return new ResultDTO();
    }

    // 파일 리스트
    @RequestMapping(value = "/list", method = RequestMethod.GET)
    public ResultDTO searchFileList(FileDTO fileDTO) throws Exception{
        return res;
    }

    // 파일 단건조회
    @RequestMapping(value = "/{fileNo}", method = RequestMethod.GET)
    public ResultDTO searchFile(@PathVariable final int fileNo) throws Exception{
        return res;
    }
}
```

---

# 5. 배포

## 5.1 스프링 부트 WAR로 배포하기

### WAR로 빌드하기

SpringBootServletInitializer 상속받기

```java
@SpringBootApplication
public class BootsampleApplication extends SpringBootServletInitializer {

    public static void main(String[] args) {
        SpringApplication.run(BootsampleApplication.class, args);
    }

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        return builder.sources(BootsampleApplication.class);
    }
}
```

### 톰캣 설정 변경

- 톰캣 기본 포트인 8080을 이미 사용하고 있는 경우

    → 설정파일에서 포트 변경

- 톰캣 내 /webapps 가 아닌 다른 폴더에 있는 프로젝트 실행하려는 경우

    → 톰캣 폴더 설정 변경