---
layout: default
title: JPA
parent: Java
nav_order: 2
---

# JPA(Java Persistence API)

* [JPA란?](#JPA란?)
* [ORM(O/R Mapper)이란?](#ORM(O/R-Mapper)이란?)
    * [SQL Mapper](#SQL-Mapper)
    * [ORM](#ORM(Object-Relation-Mapping/객체-관계-매핑))
* [JDBC](#JDBC)
* [JPA 동작 과정](#JPA-동작-과정)
    * [Insert](#Insert)
    * [Find](#Find)
* [JPA 특징](#JPA-특징)
* [JPA를 왜 사용할까?](#JPA를-왜-사용할까?)


<img src="https://media.vlpt.us/images/adam2/post/099e1c78-ad02-4c38-981e-cee526f50cf5/Untitled.png">

## JPA란?
- 자바 ORM 기술에 대한 표준 명세
- JAVA에서 제공하는 API(스프링에서 제공하는 것이 아님)
- 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스
    - JPA는 말 그대로 interface이다. 기능을 하는 라이브러리가 아님!
    - Spring PSA에 의해서 표준 인터페이스를 주었는데, 그 중 ORM을 사용하기 위해 만든 인터페이스가 바로 JPA이다.
- 기존 EJB에서 제공되던 ```Entity``` Bean을 대체하는 기술
- ORM이기 때문에 자바 클래스와 DB테이블을 매핑한다.(SQL을 매핑하지 않는다.)

## ORM(O/R Mapper)이란?
### SQL Mapper와 ORM
자바에서 DB를 사용하면 JDBC가 가장 먼저 떠오른다. JPA와 JDBC의 차이점에 대해서 알아보자.

- ORM은 DB 테이블을 자바 객체로 매핑함으로써 객체간의 관계를 바탕으로 SQL을 자동으로 생성한다.
Mapper는 SQL을 명시해주어야 한다.
- ORM은 RDB의 관계를 Object에 반영하는 것이 목적이라면, Mapper는 단순히 필드를 매핑시키는 것이 목적이라는 점에서 지향점의 차이가 있다.

### SQL Mapper
- SQL ←mapping→ Object 필드
- SQL 문으로 직접 디비를 조작한다.
- Mybatis, jdbcTemplate

### ORM(Object-Relation Mapping/객체-관계 매핑)
- DB 데이터 ←mapping→ Object 필드
    - 객체를 통해 간접적으로 DB 데이터를 다룬다.
- 객체와 디비의 데이터를 자동으로 매핑해준다.
    - SQL query가 아니라 method로 데이터를 조작할 수 있다.
    - 객체간의 관계를 바탕으로 SQL을 자동으로 생성한다.
- Persistant API라고 할 수 있다.
- JPA, Hibernate

## JDBC
<img src="https://media.vlpt.us/images/adam2/post/3fd5120b-be5a-4a87-8ec0-a35e2bb53174/Untitled%201.png">

JDBC는 DB에 접근할 수 있도록 자바에서 제공하는 API이다.

모든 JAVA Data Access 기술의 근간이다. → 모든 Persistance Framework는 내부적으로 JDBC API를 이용한다.

## JPA 동작 과정

<img src="https://media.vlpt.us/images/adam2/post/cde32cd8-b9c0-49c4-bf99-b58c0b0c2e18/Untitled%203.png">

JPA는 애플리케이션과 JDBC 사이에서 동작한다.
개발자가 JPA를 사용하면, JPA 내부에서 JDBC API를 사용하여 SQL을 호출하여 DB와 통신한다.
즉, 개발자가 직접 JDBC API를 쓰는 것이 아니다.

### Insert
<img src="https://media.vlpt.us/images/adam2/post/4c17dbbd-79d3-4728-9d8c-83b64a602303/Untitled%204.png">
MemberDAO에서 객체를 저장하고 싶을 때 개발자는 JPA에 Member 객체를 넘긴다.

JPA는
1. Member 엔티티를 분석한다.
2. INSERT SQL을 생성한다.
3. JDBC API를 사용하여 SQL을 DB에 날린다.

### Find
<img src="https://media.vlpt.us/images/adam2/post/b579405a-fca9-4925-a418-1f2bcac68597/Untitled%205.png">

JPA는
1. 엔티티의 매핑 정보를 바탕으로 적절한 SELECT SQL을 생성한다.
2. JDBC API를 사용하여 SQL을 DB에 날린다.
3. DB로부터 결과를 받아온다.
4. 결과(ResultSet)를 객체에 모두 매핑한다.
5. 쿼리를 JPA가 만들어 주기 때문에 Object와 RDB 간의 패러다임 불일치를 해결할 수 있다.

## JPA 특징
- 데이터를 객체지향적으로 관리할 수 있기 때문에 개발자는 비즈니스 로직에 집중할 수 있고 객체지향 개발이 가능하다.
- 자바 객체와 DB table사이의 매핑 설정을 통해 SQL을 생성한다.
- 객체를 통해 쿼리를 작성할 수 있는 JPQL(Java Persistence Query Language)를 지원한다.
- JPA는 성능 향상을 위해 지연 로딩이나 즉시 로딩과 같은 몇가지 기법을 제공하는데 이것을 잘 활요하면 SQL을 직접 사용하는 것돠 유사한 성능을 얻을 수 있다.
## JPA를 왜 사용할까?
1. SQL 중심적인 개발에서 객체 중심적인 개발이 가능하다.
SQL 코드의 반복, 객체지향과 관계지향 데이터베이스의 패러다임 불일치

2. Object와 RDB 간의 패러다임 불일치 해결

3. 생산성 증가

간단한 메소드로 CRUD가 가능하다.

3. 유지보수가 쉽다
기존: 필드 변경 시 모든 SQL을 수정해야 한다.
JPA: 필드만 추가하면 된다. SQL은 JPA가 처리하기 때문에 손댈 것이 없다.

#### Reference
https://velog.io/@adam2/JPA%EB%8A%94-%EB%8F%84%EB%8D%B0%EC%B2%B4-%EB%AD%98%EA%B9%8C-orm-%EC%98%81%EC%86%8D%EC%84%B1-hibernate-spring-data-jpa
