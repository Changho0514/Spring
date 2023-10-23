# Spring 정리

# SpringFramework 등장 배경

- EJB(Enterprise JavaBean)를 사용하면 애플리케이션 작성을 쉽게 할 수 있다.
- Low Level의 트랜잭션, 상태관리, 멀티 쓰레딩, 리소스 풀링과 같은 복잡한 Low Level의 API 따위를 이해하지 못해도 아무 문제 없다.

## EJB 현실 반영의 한계

- 코드 수정 후 반영하는 과제가 거창하다. ⇒ 기능은 좋지만 효율성 떨어짐.
- 테스트에도 반드시 EJB 서버가 필요하다

## 웹사이트 크기 커져 엔터프라이즈급 서비스 필요

### EJB 는 엔터프라이즈급 서비스에서 좋다.

### 장점

- 세션 빈에서 Transaction 관리 용이
- 로깅, 분산처리, 보안 등

### 단점

- EJB 스펙에 따라 코드 작성 → POJO를 변경해야함
- 컨테이너에 배포를 해야 테스트가 가능 → 개발 속도 저하
- 배우기 어렵다. 설정 복잡
- RMI 기반 서버 ⇒ 무거운 컨테이너

<aside>
💡 **`엔터프라이즈 어플리케이션도 EJB 사용안하고 만들어보자!!`**

</aside>

- **AOP, DI 같은 새로운 프로그래밍 방법론 가능.**
- **POJO로 전언적 프로그래밍 모델 가능!!!**

## 시대의 변화

### POJO + 경량 프레임 워크 선호

<aside>
💡 `POJO(Plain Old Java Object)`

→ 특정 프레임워크나 기술에 의존적이지 않은 자바 객체
→ 특정 기술에 종속적이지 않다? == 생산성, 이식성 향상
Plain : Component interface를 상속받지 않는다 == 특정 framework에 종속되지 않는다
Old : EJB 이전 java class

</aside>

<aside>
💡 `경량 프레임워크` 
→ Hibernate, JDO, iBatis(MyBatis), Spring

</aside>

### POJO + 경량 프레임 워크 장점

- 거창한 컨테이너 필요 X
- 오픈소스 → 무료
- 상당히 많은 라이브러리 지원
- 스프링 프레임워크 : 모든 플랫폼에서 사용가능

# Spring Framework

- 엔터프라이즈급 애플리케이션을 만들기 위한 모든 기능 종합적 제공. 경량화된 솔루션.
- JEE(Java Enterprise Edition) 이 제공하는 다수 기능 지원 → JEE 대체
- JEE의 다양한 기능 제공 + DI + AOP → Spring

> 개발자가 복잡하고 실수하기 쉬운 Low level에 신경쓰지 않고 
Business Logic 개발에 전념할 수 있게 해준다.
> 

# Spring의 구조

![Untitled](Spring/images/Untitled.png)

![Untitled](Spring/images/Untitled%201.png)

## POJO (Plain Old Java Object)

- 특정 환경이나 기술에 종속적이지 않은, 객체지향의 원리에 충실한 자바객체
- 테스트에 용이하다. 객체지향 설계 자유롭게 적용 가능.

## PSA(Portable Service Abstraction)

- 잘 만든 인터페이스.
- **트랜잭션 추상화, OXM 추상화, 데이터 액세스의 Exception 변환 기능 등**
- **`환경, 세부기술 변경과 관계 없는 일관된 방식`**

## IoC/DI

- DI → 유연하게 확장 가능한 객체를 만들어두고 객체간 의존관계는 외부에서 동적 설정
- IoC → 관계의 역전. 바깥에서 적절한 객체를 주게끔 한다.

## AOP(Aspect Oriented Programming)

- 관심사의 분리를 통해 소프트웨어 모듈성 향상
- 공통 모듈을 여러 코드에 쉽게 적용 가능

# SpringFramework 특징

- 경량 컨테이너
    - 스프링은 자바 객체를 담고 있는 컨테이너 이다.
    - 스프링 컨테이너는 자바 객체의 생성과 소멸과 같은 라이프 사이클을 관리한다.
    - 언제든지 스프링 컨테이너로부터 필요한 객체를 가져와 사용할 수 있다.
    
- DI(Dependency Injection - 의존성 주입) 패턴 지원
    - 설정파일, 어노테이션을 통해서 객체 간의 의존 관계를 설정할 수 있다.
    - 객체는 의존하고 있는 객체를 직접 생성하거나 검색할 필요가 없다.
    
- AOP(Aspect Oriented Programming) 지원
    - AOP는 문제를 바라보는 관점을 기준으로 프로그래밍하는 기법이다.
    - 핵심 관심사항(문제해결) 과 공통 관심사항(전체 적용) 을 기준으로 프로그래밍 한다.
    - 여러 공통 모듈을 여러 코드에 쉽게 적용할 수 있게 한다.
    - Spring은 자체적 프록시 기반 AOP 지원한다 → 트랜잭션, 로깅, 보안과 같이 여러 모듈에서 공통적으로 필요하나 실제 모듈의 핵심이 아닌 기능을 분리해 적용 가능.
    
- POJO(Plain Old Java Object) 지원
    - 특정 인터페이스 구현, 클래스 상속하지 않는 일반 자바 객체를 지원한다.
    - 스프링 컨테이너에 일반 자바 객체로 사용 가능하다는 것.
    - 즉, 일반 자바객체 사용가능!
    
- IoC(Inversion of Control) - 제어의 반전
    - IoC는 스프링이 갖는 핵심 기능이다.
    - 예전에 개발자가 자바객체의 생성, 의존관계를 모두 설정했다.
    - Servlet, EJB가 나타나며 Servlet Container, EJB Container에게 제어권을 준다.
    - Servlet, EJB 제외한 나머지 객체 제어권은 개발자들이 담당하고 있었다 .
    - 스프링에서는 객체 생성, 생명주기 관리 할 수 있다. 그래서 Spring Container, IoC Container 라고 부르기도 한다.

- 트랜잭션 처리를 위한 일관된 방법 제공
    - JDBC, JTA, 컨테이너가 제공하는 트랜잭션을 사용하든 설정파일을 통해 트랜잭션 관련정보를 입력하기에 트랜잭션 구현에 상관없이 동일한 코드를 여러 환경에서 사용가능>?>??
    
- 영속성과 관련된 다양한 API 지원
    - JDBC, iBatis, MyBatis, Hibernate, JPA 등 DB 처리를 위해 사용되는 라이브러리와 연동 지원.
    
- 다양한 API 연동 지원
    - JMS, 메일, 스케줄링 지원
    

# SpringFramework Module

![Untitled](Spring/images/Untitled%202.png)

1. `Spring Core` : 핵심 기능 제공, 주요 컴포넌트 : Bean Factory. Spring을 컨테이너로 만들었다.
2. Spring Context:  Context module은 Spring을 Framework로 만들었다. application 생명주기 이벤트, 유효성 검증 등 제공
3. Spring AOP : 설정 관리를 통해 AOP 기능을 Spring Framework 과 통합.
4. Spring DAO : Spring JDBC DAO 추상 레이어. 예외 핸들링
5. Spring ORM: ORM framework 과 플러그인 → JDO, Hibernate, iBatis 제공
6. Spring Web: Application Context module 상위에 구현 → web기반 application에 context 제공.
7. Spring Web MVC: 자체적으로 MVC 프레임워크 제공.

# IoC(Inversion of Control, 제어의 역행)

- 객체지향 언어에서 Object 간의 연결 관계를 런타임에 결정
- 객체 간 관계가 느슨하게 연결됨(Loose Coupling)
- IoC 구현 방법 중 하나가 DI(Dependency Injection)

- 먼저 Dependency Lookup 해서 컨테이너를 조회하고 Object를 Lookup 한다.
- DI
    
    ![Untitled](Spring/images/Untitled%203.png)
    
    - 컨테이너가 직접 의존 구조를 Object에 설정할 수 있게 지정.
    Object가 컨테이너 존재 여부 알 필요 없음
    - Setter Injection, Constructor Injection
    

# Container

- 객체의 생성, 사용, 소멸에 해당하는 라이프사이클을 담당한다.
- 라이프사이클을 기본으로 애플리케이션 사용에 필요한 주요 기능을 제공한다.

## 기능

- 라이프 사이클 관리
- Dependency 객체 제공
- Thread 관리
- 기타 애플리케이션 실행에 필요한 환경

## 필요성

- 비즈니스 로직 외에 부가적인 기능들에 대해서는 독립적으로 관리되기 위함
- 서비스 look up, Configuration에 대한 일관성을 위해
- 서비스 객체를 사용하기 위해 각각 Factory, Singleton 패턴을 구현하지 않아도 된다.

## IoC Container

- 오브젝트 생성, 관계설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 독립된 컨테이너가 담당한다.
- 컨테이너가 코드(개발자) 대신 오브젝트에 대한 제어권을 갖는다 → IoC라고 부른다.
- 스프링 컨테이너를 IoC 컨테이너라고 부르기도 함.
- BeanFactory, ApplicationContext가 있다.

### IoC의 장점 : 객체간 결합도 떨어뜨림
→ 유지보수 될 때 그 클래스와 결합된 다른 클래스 유지보수 필요 없다.

## DI Container

- DI Container가 관리하는 객체를 Bean(빈) 이라고 하고, 이 빈들의 라이프사이클을 관리하는 의미로 빈팩토리(BeanFactory)라고 한다.
- Bean Factory에 여러 기능을 추가해 ApplicationContext로 사용한다.

![Untitled](Spring/images/Untitled%204.png)

# 강한 결합

![Untitled](Spring/images/Untitled%205.png)

- **MemberService, AdminService 교체 or 내부코드 변경시 위의 클래스까지 수정해야 한다.**

## IoC 적용

![Untitled](Spring/images/Untitled%206.png)

- 다형성 적용 → 인터페이스 호출
- 구현 클래스 교체가 용이하다.
- But, 인터페이스 교체시 호출 클래스도 수정해야 한다.

![Untitled](Spring/images/Untitled%207.png)

## 팩토리 방식 적용

![Untitled](Spring/images/Untitled%208.png)

- 팩토리가 구현 클래스 생성.
- 인터페이스 변경 시 팩토리만 수정하면 된다. 호출클래스는 변경 하지 않아도 된다.
- But, 클래스에 팩토리 호출하는 소스가 들어가야 한다 → 팩토리에 의존하네

![Untitled](Spring/images/Untitled%209.png)

## Assembler 적용

![Untitled](Spring/images/Untitled%2010.png)

- 팩토리 패턴의 장점 더한다. 어떠한 것에도 의존 X
- 실행시점(Runtime) 에 클래스 간의 관계가 형성

![Untitled](Spring/images/Untitled%2011.png)

Spring Container가 외부조립기(Assembler) 역할을 한다.

# DI 용어정리

## Bean

- 스프링이 IoC 방식으로 관리하는 오브젝트
- 스프링이 직접 그 생성과 제어 담당하는 오브젝트만 Bean이라고 부른다.

## BeanFactory

- 스프링이 IoC를 담당하는 핵심 컨테이너이다.
- Bean 등록, 생성, 조회, 반환 담당
- 일반적으로는 이를 확장한 ApplicationContext 사용

## ApplicationContext

- BeanFacotry 확장한 IoC 컨테이너.
- 부가 서비스 제공.

## Configuration metadata

- Application Context 또는 BeanFactory가 IoC 적용하기 위해 사용하는 메타정보.
- Bean 객체 생성, 구성할때 사용된다.

![Untitled](Spring/images/Untitled%2012.png)

# 빈 생성 범위

## 싱글톤 빈(Singleton Bean)

- 스프링 빈은 기본적으로 싱글톤으로 만들어진다.
- 컨테이너가 제공하는 모든 빈의 인스턴스는 동일하다
- scope - prototype으로 설정하면 항상 새로운 인스턴스 반환

![Untitled](Spring/images/Untitled%2013.png)

| Singleton | 컨테이너당 하나의 인스턴스 빈만 생성한다 (default) |
| --- | --- |
| Prototype | 요청할때마다 새로운 빈 인스턴스 생성 |
| request | HTTP Request 별로 새로운 인스턴스 생성 |
| Session | HTTP session 별로 새로운 인스턴스 생성 |

![Untitled](Spring/images/Untitled%2014.png)

## XML

: xml 문서로 메타정보 기술. 단순, 사용하기 쉬움

![Untitled](Spring/images/Untitled%2015.png)

## Annotation

- 어플리케이션 규모 커지고 빈 갯수 많아지면 XML로 관리가 어렵다.
- Annotation 부여시 자동으로 빈 등록 가능.
- Object Bean 스캐너로 빈 스캐닝을 통해 자동 등록.
- 일반적으로 **클래스 이름을 빈의 아이디로 사용한다. (첫 글자만 소문자)**

![Untitled](Spring/images/Untitled%2016.png)

- Annotation으로 빈 설정시 반드시 Component-scan을 설정해야 한다.

![Untitled](Spring/images/Untitled%2017.png)

![Untitled](Spring/images/Untitled%2018.png)

![Untitled](Spring/images/Untitled%2019.png)

## XML로 빈 객체 생성, 주입하기

![Untitled](Spring/images/Untitled%2020.png)

name : 주입 받을 곳에서 호출 할 이름 설정

id : 주입 받을 곳에서 호출할 이름 설정(유일)

class : 주입할 클래스

## XML 사용

![Untitled](Spring/images/Untitled%2021.png)

# 스프링 빈 의존 관계 설정

## Constructor - XML이용!

- 객체 또는 값을 생성자를 통해 주입 받는다.
- <constructor-arg> : <bean> 의 하위태그로 설정한 bean 객체 or 값을 생성자를 통해 주입하도록 설정한다.

![Untitled](Spring/images/Untitled%2022.png)

![Untitled](Spring/images/Untitled%2023.png)

![Untitled](Spring/images/Untitled%2024.png)

**name = “position” 처럼 설정해주어야 한다.**

![Untitled](Spring/images/Untitled%2025.png)

argument 순서 지키지 않는 경우 

![Untitled](Spring/images/Untitled%2026.png)

## Property - XML이용!

- `Setter Method` - Setter 를 통해서는 하나만 받을 수 있다

![Untitled](Spring/images/Untitled%2027.png)

![Untitled](Spring/images/Untitled%2028.png)

![Untitled](Spring/images/Untitled%2029.png)

![Untitled](Spring/images/Untitled%2030.png)

![Untitled](Spring/images/Untitled%2031.png)

![Untitled](Spring/images/Untitled%2032.png)

![Untitled](Spring/images/Untitled%2033.png)

![Untitled](Spring/images/Untitled%2034.png)

**@Autowired**는 SpringFramework에 종속적이라는 것 기억!!

![Untitled](Spring/images/Untitled%2035.png)

→ 예전거임.

![Untitled](Spring/images/Untitled%2036.png)

→ 최근거. Framework 종속 X일때는 @Inject 사용 권장

## @Resource 사용

### 1. 멤버변수에

![Untitled](Spring/images/Untitled%2037.png)

### 2. Setter 로

![Untitled](Spring/images/Untitled%2038.png)

## @Autowired 사용

### 1. 생성자에

![Untitled](Spring/images/Untitled%2039.png)

- 동일한 타입의 bean이 여러개면 @Qualifier(”name”)으로 식별

### 2. 필드에

![Untitled](Spring/images/Untitled%2040.png)

- 동일한 타입의 bean이 여러개면 @Qualifier(”name”)으로 식별

### 3. 일반 메서드에

![Untitled](Spring/images/Untitled%2041.png)

- 동일한 타입의 bean이 여러개면 @Qualifier(”name”)으로 식별

## 빈 객체의 생성 단위(scope)

![Untitled](Spring/images/Untitled%2042.png)

## 스프링 빈의 생명주기

![Untitled](Spring/images/Untitled%2043.png)

# AOP 개요

`핵심 관심사항과 공통 관심사항`

**여러 모듈 적용에 중복된 코드 없애기**

**`핵심적인 기능에서 부가적인 기능을 분리한다.`**

## 적용 예

### 1. 간단한 메소드의 성능검사

- DB에 대량의 데이터를 넣고 빼는 등의 배치 작업에 대하여 시간을 측정해보고 쿼리를 개선하는 작업이 의미 있다.
- 모든 메서드 처음 과 끝에 시간 찍는거 추가하기는 번거롭다.
- 해당 작업 코드 밖에서 설정하고 사용하기

### 2. 트랜잭션 처리

- 트랜잭션은 비즈니스 로직 전후에 설정.
- try-catch 등을 부가적인 기능으로 분리해서 처리

### 3. 예외 반환

- 구조가 별로 안좋은 예외들이 발생했을 때 그것을 잘 정의되어있는 예외 계층 구조로 변환해서 던지기

### 4. 아키텍쳐 검증

### 5. 기타

- 하이버네이트 + JDBC 사용시 DB 동기화 문제 해결
- 멀티 쓰레드 safety 관련해서 작업하는 경우 메서드들에 일괄적으로 락을 설정
- 데드락 등으로 인한 예외를 만났을때 재시도
- 로깅, 인증, 권한

## AOP 구조

![Untitled](Spring/images/Untitled%2044.png)

**핵심 관심사항에 공통 관심사항인 보안, 트랜잭션, 로깅 등을 어떻게 적용시킬 것인지 생각하는 것이 실력이다.**

# Spring AOP

## Target

- 핵심 기능을 담고 있는 모듈. target은 부가 기능을 부여할 대상이 된다.

## Advice

- 어느시점(ex: method의 수행 전/후, 예외 발생 후) 에 어떤 공통 관심기능을 적용할지 정의한 것. Target에 제공할 부가기능을 담는 모듈

## JoinPoint

- Aspect가 적용될 수 있는 지점 (method, field)
- target 객체가 구현한 인터페이스의 모든 method 는 Join Point가 된다.

## PointCut

- 공통 관심 사항이 적용될 JoinPoint

## Aspect

- 여러 객체에서 공통으로 적용되는 공통 관심 사항(transaction, loggin, security)
- AOP의 기본 모듈
- Aspect = Advice + PointCut
- singleton 형태의 객체로 존재한다.

## Advisor

- Advisor = Advice + pointCut
- Spring AOP에서만 사용되는 특별한 용어.

## Weaving

- 어떤 Advice를 어떤 PointCut에 적용시킬 것인지에 대한 설정(Advisor)
- Pointcut에 의해 결정된 타겟의 JoinPoint에 부가기능(Advice)를 삽입하는 과정
- AOP의 핵심기능(Target)의 코드에 영향을 주지 않으면서 필요한 부가기능(Advice)를 추가할 수 있도록 해주는 핵심적인 처리 과정.

![Untitled](Spring/images/Untitled%2045.png)

![Untitled](Spring/images/Untitled%2046.png)

![Untitled](Spring/images/Untitled%2047.png)

# Spring AOP 특징

## 1. Spring은 프록시 기반 AOP를 지원한다.

- Spring은 Target 객체에 대한 Proxy를 만들어 제공한다.
- Target을 감싸는 Proxy는 실행시간(Runtime)에 생성된다.
- Proxy는 Advice를 Target 객체에 적용하면서 생성되는 객체이다.

![Untitled](Spring/images/Untitled%2048.png)

## 2. 프록시가 호출을 가로챈다 (Intercept)

- Proxy는 Target 객체에 대한 호출을 가로챈 다음 Advice의 부가 기능 로직을 수행하고 난 후 Target의 핵심 기능 로직을 호출한다(전처리)
- 또는 Target의 핵심 기능 로직method를 호출한 뒤에 부가기능(Advice)를 수행하는 경우도 있다. (후처리)

![Untitled](Spring/images/Untitled%2049.png)

## 3. Spring AOP는 method JoinPoint만 지원한다.

- Spring은 동적 Proxy를 기반으로 AOP 구현 → method JoinPoint만 지원한다.
- 즉, 핵심기능(Target)의 method가 호출되는 런타임 시점에만 부가기능(Advice) 적용가능
- AspectJ와 같은 고급 AOP framework가 객체 생성, 필드값의 조회와 조작, static method 호출 및 초기화 등에 부가 기능을 적용할 수 있는 것과 비견된다.

# Spring AOP 구현 방법

- POJO Class
- Spring API
- Annotation

## 1. POJO 기반

### 우선, XML Schema 확장 기법을 통해 설정 파일 작성

1. `AOP namespace, XML Schema 추가`

![Untitled](Spring/images/Untitled%2050.png)

1. aop namespace로 설정한다.

![Untitled](Spring/images/Untitled%2051.png)

### 설정태그

![Untitled](Spring/images/Untitled%2052.png)

### 설정파일<aop:aspect>

- 한 개의 Aspect(공통 관심 기능) 설정
- ref 속성을 통해 공통 기능 갖고 있는 bean을 연결
- id는 이 태그의 식별자 설정
- 자식 태그로 <aop:pointcut> advice 관련 태그가 올 수 있다.

### 설정 파일<aop:pointcut>

- PointCut(공통 기능이 적용될 곳)을 지정하는 태그
- <aop:config> 나 <aop:aspect> 의 자식태그
    - <aop:config> : 전역적으로 사용
    - <aop:aspect> : 내부에서 사용
- 속성 :
    - id: 식별자로 advice 태그에서 사용됨.
    - expression: pointcut 지정

![Untitled](Spring/images/Untitled%2053.png)

## 그 다음, POJO 기반으로 Advice Class를 작성한다.

- 설정 파일의 advice 관련 태그에 맞게 작성
- bean으로 등록하며 <aop:aspect> ref 속성으로 참조.

### Advice 정의 관련 태그

- pointcut: 직접 pointcut을 설정. 호출 할 mehtod의 패전 지정
- pointcut-ref: <aop:pointcut> 태그의 id명을 넣어 pointcut 지정
- method: Aspect bean에서 호출할 mehtod 명 지정.

### 특징

- class 명, method 명에 대한 제한은 없다.
- method 구문은 호출되는 시점에 따라 달라질 수 있음

### Before Advice

- 대상 객체의 메서드가 실행되기 전에 실행됨.
- return type: 리턴값 가져도 실제 advice 적용 과정에서 사용X → void 사용
- argument : 없거나, 호출되는 메서드에 대한 정보 or 파라미터 정보. 필요하면 joinPoint

![Untitled](Spring/images/Untitled%2054.png)

1. 빈 객체를 사용하는 코드에서 스프링이 생성한 AOP 프록시의 메서드 호출
2. AOP 프록시는 <aop:before> 에서 지정한 메서드 호출
3. AOP 프록시는 Aspect 기능 실행 후 실제 빈 객체의 메서드 호출

### after Returning Advice

- 대상 객체의 method 실행이 `정상적으로` 끝난 뒤 실행된다.
- return type: void
- argument:
    - 없거나 JoinPoint. JoinPoint는 항상 첫 argument
    - 특정 객체 타입 값을 argument로 받을 수 있다.

![Untitled](Spring/images/Untitled%2055.png)

![Untitled](Spring/images/Untitled%2056.png)

1. 빈 객체를 사용하는 코드에서 스프링이 생성한 AOP 프록시의 메서드 호출
2. AOP 프록시는 실제 빈 객체의 메서드 호출(정상 실행)
3. AOP 프록시는 <aop:after-returning> 에서 지정한 메서드 호출

### after Throwing advice

- 대상 객체의 method 실행 중 예외가 발생한 경우 실행
- return type: void
- argument:
    - 없거나 JoinPoint. JoinPoint는 항상 첫 argument
    - 특정 객체 타입 값을 argument로 받을 수 있다.

![Untitled](Spring/images/Untitled%2057.png)

![Untitled](Spring/images/Untitled%2058.png)

1. 빈 객체를 사용하는 코드에서 스프링이 생성한 AOP 프록시의 메서드 호출
2. AOP 프록시는 실제 빈 객체의 메서드 호출(exception 발생)
3. AOP 프록시는 <aop:after-throwing> 에서 지정한 메서드 호출

### after advice

- 정살 실행, exception 발생 여부와 상관 없이 메서드 실행 종료 후 공통 기능 적용
- return type: void
- argument:
    - 없거나 JoinPoint. JoinPoint는 항상 첫 argument
    - 특정 객체 타입 값을 argument로 받을 수 있다.

![Untitled](Spring/images/Untitled%2059.png)

![Untitled](Spring/images/Untitled%2060.png)

1. 빈 객체를 사용하는 코드에서 스프링이 생성한 AOP 프록시의 메서드 호출
2. AOP 프록시는 실제 빈 객체의 메서드 호출(정상 실행, exception 발생 : `java의 finally와 같다`)
3. AOP 프록시는 <aop:after> 에서 지정한 메서드 호출

### around Advice

- 위의 네가지 advice 를 다 구현 가능
- return type: Object
- argment:
    - 반드시 “org.aspectj.lang.ProceedingJoinPoint”를 첫 argument로 지정.

![Untitled](Spring/images/Untitled%2061.png)

![Untitled](Spring/images/Untitled%2062.png)

1. 빈 객체를 사용하는 코드에서 스프링이 생성한 AOP 프록시의 메서드 호출
2. AOP 프록시는 <aop:around> 에서 지정한 메서드 호출
3. AOP 프록시는 실제 빈 객체의 메서드 호출
4. AOP 프록시는 <aop:around> 에서 지정한 메서드 호출

## JoinPoin class 구성 요소

- 대상 객체에 대한 정보를 가지고 있는 객체. Spring Container로부터 받는다.
- org.aspectj.lang 패키지에 있음.
- 반드시 Aspect method의 첫 argument로 와야함.

![Untitled](Spring/images/Untitled%2063.png)

## @aspect Annotation을 이용한 AOP 구현

- @Aspect Annotation을 이용해 Aspect Class에 직접 Advice 및 PointCut 설정
- 설정 파일에 `<aop:aspectj-autoproxy/>` 추가해야함
- Aspect Class를 <bean> 으로 등록
- 어노테이션
    - @Aspect: Aspect Class 선언
    - @Before(”pointcut”)
    - @AfterReturning(pointcut=””, returning=””)
    - @AfterThrowing(pointcut=””, throwing=””)
    - @After(”pointcut”)
    - @Around(”pointcut”)
- Around 를 제외한 나머지 method들은 첫 argument로 JoinPoint를 가질 수 있다.
- Around Method는 argument 로 ProceedingJoinPoint를 가질 수 있다.

![Untitled](Spring/images/Untitled%2064.png)

# MVC

### Model

- 어플리케이션 상태의 캡슐화
- 상태 쿼리에 대한 응답
- 어플리케이션의 기능 표현
- 변경을 view에 통지

### View

- 모델을 화면에 시각적으로 표현
- 모델에게 업데이트 요청
- 사용자의 입력을 컨트롤러에 전달
- 컨트롤러가 view를 선택하도록 허용

### Controller

- 어플리케이션의 행위 정의
- 사용자 액션을 모델 업데이트와 mapping
- 응답에 대한 view 선택

`**확장성을 위해 Model, View, Controller 세 영역으로 분리**`

- 컴포넌트 변경이 다른 영역 컴포넌트에 영향 미치지 않는다 → 유지보수 용이
- 컴포넌트간 결합성 낮음 → 확장성 뛰어남

### 장점

- 화면과 비즈니스 로직을 분리하여 작업 가능
- 영역별 개발로 인해 확장성 뛰어남
- 표준화된 코드 사용 → 공동작업 용이, 유지보수성 좋음

### 단점

- 개발과정 복잡 → 초기개발 속도  늦음
- 어려움

## Model 2의 요청 흐름

![Untitled](Spring/images/Untitled%2065.png)

## Spring MVC 특징

Spring은 DI, AOP와 같은 기능 뿐 아니라 Servlet 기반의 Web 개발을 위한 MVC Framework를 제공한다.

Model2 Architecture와 Front Controller Pattern을 Framework에서 제공한다.

Spring 기반 → Transaction 처리나 DI, AOP를 손쉽게 사용.

# Spring MVC 구성 요소

## 1. DispatcherServlet(FrontController)

- 모든 클라이언트의 요청을 전달받는다.
- controller 에게 클라이언트의 요청 전달하고, Controller가 리턴한 결과 값을 View에게 전달하여 알맞은 응답을 생성한다.

## 2. HandlerMapping

- 클라이언트의 요청 URL을 어떤 Controller가 처리할 지 결정한다
- - URL 과 요청 정보를 기준으로 어떤 핸들러 객체를 사용할지 결정하는 객체.
DispatcherServlet은 하나 이상의 핸들러 매핑을 가질 수 있다.

## 3. Controller

- 클라이언트의 요청 처리하고, Model 을 호출하고 그 결과를 DispatcherServlet에 알려준다.

## 4. ModelAndView

- Controller 가 처리한 데이터 및 화면에 대한 정보를 보유한 객체

## 5. ViewResolver

- Controller가 리턴한 뷰 이름을 기반으로 Controller의 처리 결과를 보여줄 View를 결정한다.

## 6. View

- Controller의 처리 결과를 보여줄 응답화면을 생성

## Spring MVC 요청 흐름

![Untitled](Spring/images/Untitled%2066.png)

![Untitled](Spring/images/Untitled%2067.png)

1. DispatcherServlet이 요청을 수신한다.
- 단일 front Controller Servlet
- 요청을 수신하여 처리를 다른 컴포넌트에 위임한다.
- 어느 Controller에 요청을 전송할 지 결정
2. DispatcherServlet은 HandlerMapping에 어느 Controller를 사용할 것인지 문의
- URL과 Mapping
3. DsipatcherServlet은 요청을 Controller에 전송하고 Controller 는 요청을 처리한 후 결과를 리턴한다.
- Business Logic 수행 후 결과 정보(Model)가 생성되어 JSP 같은 view에서 사용된다.
4. ModelAndView Object에 수행 결과가 포함되어 DispatcherServlet에 리턴.
5. ModelAndView는 실제 JSP 정보를 갖고있지 않으며, ViewResolver가 논리적 이름을 실제 JSP로 변환한다.
6. View는 결과 정보로 화면을 표현한다.

## Spring MVC 구현

1. web.xml에 DispatcherServlet 등록 및 Spring 설정파일 등록
2. 설정 파일에 HandlerMapping 설정
3. Controller 구현 및 Context 설정 파일(servlet-context.xml)에 등록
4. Controller와 JSP 연결을 위해 View Resolver 설정
5. JSP 코드 작성

<aside>
💡 좋은 디자인이란?
- 컨트롤러가 많은 일 하지 않고 Service에 처리 위임!!!

</aside>

### web.xml - DispatcherServlet 설정

1. <init-param> 을 설정하지 않으면 “<servlet-name>-servlet.xml” 파일에서 applicationbContext 정보를 load한다.
2. Spring Container는 설정파일의 내용을 읽고 ApplicationContext 객체를 생성한다.
3. <url-pattern>은 DispatcherServlet이 처리하는 URL Mapping pattern을 정의한다. 
4. Servlet이므로 1개 이상의 DispatcherServlet 설정 가능
5. <load-on-startup>1</load-on-startup> 설정 시 WAS startup할때 초기화 작업 진행한다.

![Untitled](Spring/images/Untitled%2068.png)

![Untitled](Spring/images/Untitled%2069.png)

![Untitled](Spring/images/Untitled%2070.png)

![Untitled](Spring/images/Untitled%2071.png)

![Untitled](Spring/images/Untitled%2072.png)

![Untitled](Spring/images/Untitled%2073.png)

![Untitled](Spring/images/Untitled%2074.png)

# Controller

@Controller 와 @RequestMapping 선언

- method 단위의 mapping 이 가능하다.
- Client의 요청을 처리한다.

**이렇게 어노테이션의 사용을 장려한다.**

![Untitled](Spring/images/Untitled%2075.png)

![Untitled](Spring/images/Untitled%2076.png)

![Untitled](Spring/images/Untitled%2077.png)

**`base-package에 설정된 package 내의 class 중 @Controller annotation이 적용된 클래스는 자동 스캔 대상이 된다.`**

Controller에서 @RequestMapping 선언

![Untitled](Spring/images/Untitled%2078.png)

![Untitled](Spring/images/Untitled%2079.png)

![Untitled](Spring/images/Untitled%2080.png)

## 진짜 중요한 기능!!!

- HTML form 과 Command Object(DTO, VO..)
    
    springMVC는 form에 입력한 data를 JavaBean 객체를 이용해서 전송할 수 있다.
    

![Untitled](Spring/images/Untitled%2081.png)

**`이름이 같다면 알아서 맞춰서 넣어준다`**

정말 엄청나게 편리하다!

![Untitled](Spring/images/Untitled%2082.png)

## **`@ModelAttribute를 사용하면 View에서 사용할 command 객체의 이름을 변경할 수 있다!!`**

![Untitled](Spring/images/Untitled%2083.png)

**@RequestBody**

→ 처리 가능한 변환기가 자동으로 객체로 변환시켜줌.

- **주로 @ResponseBody와 함께 사용됨 → 비동기 처리**

# View

- Controller에서는 처리 결과를 보여줄 View 이름이나 객체 리턴
DispatcherServlet은 View이름이나 View 객체를 이용하여 View 생성

![Untitled](Spring/images/Untitled%2084.png)

- ViewResolver : 논리적 view와 실제 JSP 파일 mapping 한다.
    - servlet-context.xml
    
    ![Untitled](Spring/images/Untitled%2085.png)
    
    ![Untitled](Spring/images/Untitled%2086.png)
    
    3가지 경우 모두 가능하다.
    

## 자동 지정

- 유형
    - return type이 Model이나 Map인 경우

![Untitled](Spring/images/Untitled%2087.png)

## redirect view

- view 이름에 “redirect:”를 붙이면 지정한 페이지로 redirect 된다.

![Untitled](Spring/images/Untitled%2088.png)

# Model

- View에 전달하는 data

## Model 생성

- @RequestMapping annotation이 적용된 method의 Map, Model, ModelMap
- @RequestMapping method가 return 하는 ModelAndView
- @ModelAttribute annotation이 적용된 method가 return 한 객체

![Untitled](Spring/images/Untitled%2089.png)

## ModelAndView 이용

![Untitled](Spring/images/Untitled%2090.png)

## @ModelAttribute 를 이용

- @RequestMapping annotation이 적용되지 않은 별도 method로 모델이 추가될 객체를 생성한다.
- 모델을 추가하고 싶을 때 사용

## 요청 URL 매칭

![Untitled](Spring/images/Untitled%2091.png)

![Untitled](Spring/images/Untitled%2092.png)

![Untitled](Spring/images/Untitled%2093.png)

# Spring Web Application의 동작 원리

![Untitled](Spring/images/Untitled%2094.png)

## 순서

1. 웹 어플리케이션이 실행되면 Tomcat(WAS)에 의해 web.xml이 loading 됨.
2. web.xml에 등록되어 있는 ContextLoaderListner(java class) 생성. ContextLoaderListener class는 ServletContextListener를 구현하며 ApplicationCotnext를 생성하는 역할 수행
3. 생성된 ContextLoaderListener는 root-context.xml을 loading
4. root-context.xml에 등록되어 있는 Spring Container 구동. 이때 개발자가 작성한 Business Logic(Service)에 대한 부분과 Database Logic(DAO), VO 객체들이 생성.
5. Client로부터 요청(request) 들어옴.
6. DispatcherServlet 생성. FrontController 역할 수행
요청 분석하여 PageController에 전달하고 응답 받아서 응답 처리 결정. 실질적 작업은 PageController에서 이뤄진다. HandlerMapping, ViewResolver 가 일함
7. DispatcherServlet은 servlet-context.xml 로딩
8. 두번째 Spring Contiainer 구동 → 응답에 알맞는 PageController 동작.
첫 Spring Container가 구동되면서 생성된 DAO, VO, Service 클래스와 협업하여 알맞은 작업 처리.
