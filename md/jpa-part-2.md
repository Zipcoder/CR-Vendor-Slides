-
## JPA Annotations

- @Entity
- @ID
- @PersistenceContext
- `@OneToMany`, `@ManyToOne`, `@OneToOne`, `@ManyToMany`
- [Full list](https://docs.oracle.com/javaee/7/api/index.html?javax/persistence/package-summary.html)

-
@Entity

- Domain objects are "entities"
- Entities are managed by the EntityManager
- Table name defaults to class name
  - use `@Table(name = "...")` to change this

-
@ID

- Sets the field (usually `int` or `long`) as the primary key
- Usually paired with `@GeneratedValue`

-
`@OneToMany`, `@ManyToOne`, `@OneToOne`, `@ManyToMany`

Indicate relationships between entities eg:

```
@Entity
public class Room{
...
@OneToMany
private List<Window> windows;
```

-
-
More about Repository methods

-
Access Sub-properties in predicates

- `findBy<PropertyName><SubpropertyName>`
- eg: `findByAddressState()`
- Optional underscore separator: `findByAddress_ZipCode()`  

-
Specify custom queries

- `@Query` annotation on method signature
- Queries written in JPQL
- Serves as a hint for the Spring-generated implementation

-
Custom query example

```Java
@Query("select c from Customer c where c.emailAddress = ?1")
Customer findByEmailAddress(EmailAddress email);
```

-
Custom implementations (example to follow)

- Create an interface to define the desired method(s)
- Implement custom JPA method in `<RepositoryName>Impl`, implementing interface
- Extend the same inteface in `<RepositoryName>`

-
Custom JPA example

```Java
interface ClassicCarUpdater {
  int updateClassics();
}

public class CarRepositoryImpl implements ClassicCarUpdater {
  @PersistenceContext
  private EntityManager em;

  public int updateClassics() {
    String update =
      "UPDATE Cars car SET car.isClassic = true " +
      "WHERE car.isClassic = false " +
      "AND car.id IN (" +
      "SELECT c from Cars c WHERE c.year < 1992)";
    return em.createQuery(update).executeUpdate();
  }
}
```

-
Custom JPA example (repository)

```Java
public interface CarRepository extends
        JPARepository<Car, Integer>,
        ClassicCarUpdater {
    ...
    }
```

-
-
Configuration hints:

- Show hibernate generated queries with `spring.jpa.show-sql=true` in `application.properties`

-
@PersistenceContext and @PersistenceUnit

- @PersistenceUnit injects an EntityManagerFactory
- @PersistenceContext injects an EntityManager
