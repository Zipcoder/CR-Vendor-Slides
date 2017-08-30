# JPA

Java Persistence API

-
## JPA Specification

- Part of Java EE spec
- Contained in the `javax.persistence` package
- Implemented by many other libraries

-
## Hibernate

- Popular implementation of JPA
- Handles mapping Entity classes to DB tables
- Included in `spring-data-jpa` dependency by default
- Finds entities with entity scanning


-
### ORM (definition)

- Object Relational Mapping
- The practice of/tool for relating objects to DB rows

-
-
## Spring repositories

-
### Repositories (Spring's DAO objects, The Way to your data)

- Part of spring framework
- Used to provide JPA implementation
- Automatically implemented by Spring Boot (during startup)
- Extend JPARepository or CRUDRepository

-
Existing repositories

- `Repository` - parent marker interface
- `CRUDRepository` - repository defines CRUD operations
- `JpaRepository` - extended from `CRUDRepository`, defines 18 methods and can contain custom methods


-
Method names parsed and automatically implemented

`<verb><subject?>By<predicate>()`  
eg: `findCarByYear()` or `countDistictPersonByLastName()`  



-
Verbs

- `get`, `read`, `find` -- queries and returns objects (synonyms)
- `count` -- returns a count of matching objects

-
Subject

- Optional
- Produces distinct query if the word `distinct` is present

-
Predicate

- references a property
- may specify [comparison operations](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#_supported_query_keywords) (`equals` is implied)
- `ignoresCase`/`ignoringCase` usable for case-insensitive comparison
- predicate properties map to arguments


-
Repositories provide indirect JPA access -- we can still directly access using `@persistencecontext`/`@entitymanager` (later)



