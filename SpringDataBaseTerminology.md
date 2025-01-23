# Object Relational Mapping (ORM) and JPA Overview

This document provides an overview of **ORM**, **JPA**, and their usage in relational and NoSQL databases.

---

## Object Relational Mapping (ORM)

- **ORM** is a technique used to map Java objects to database tables.
- It allows developers to interact with databases using object-oriented programming (OOP) concepts, reducing the complexity of working with SQL.
- Example:
    - Java Class: `User`
    - Database Table: `users`
    - ORM maps the `User` class attributes to the columns of the `users` table.

---

## Java Persistence API (JPA)

- **JPA** is a specification for ORM in Java.
- It provides interfaces and annotations that help map Java objects to relational database tables.
- **JPA** does not directly interact with the database; it requires a **persistence provider** (an ORM tool) to implement its functionality.

### Key Features of JPA:
1. Simplifies database interactions by using Java objects.
2. Provides annotations like `@Entity`, `@Table`, and `@Id` to define mappings between classes and tables.
3. Allows querying the database using JPQL (Java Persistence Query Language), a more object-oriented query language.

---

## Persistence Providers (ORM Tools)

- To use JPA, you need a **persistence provider**.
- A persistence provider is an implementation of the JPA specification that provides the underlying functionality for database interaction.
- Examples of JPA persistence providers:
    - **Hibernate**
    - **EclipseLink**
    - **OpenJPA**

---

## Spring Data JPA

- **Spring Data JPA** is a library built on top of JPA.
- It is **not a persistence provider**, but it simplifies working with JPA by providing higher-level abstractions and utilities.
- Features of Spring Data JPA:
    - Automatic repository creation using interfaces (e.g., `JpaRepository`).
    - Customizable queries using method naming conventions.
    - Support for JPQL and native SQL queries.

---

## Relational Databases (RDB) vs NoSQL Databases

### JPA and Relational Databases:
- JPA is designed for working with **relational databases (RDB)**, where data is stored in tables with fixed schemas.
- Example: MySQL, PostgreSQL, Oracle DB.

### NoSQL Databases (e.g., MongoDB):
- **MongoDB** is a NoSQL database that stores data as collections of documents.
- MongoDB is schema-less or supports flexible schemas, making it different from relational databases.

### Why JPA is Not Used for MongoDB:
- JPA is tailored for relational databases and does not support the flexible, document-based structure of MongoDB.

---

## Spring Data MongoDB

- **Spring Data MongoDB** is the persistence provider for MongoDB in Spring applications.
- It provides the necessary abstractions and implementations to work with MongoDB in a Spring-based environment.
- Features of Spring Data MongoDB:
    - Repository support similar to Spring Data JPA for MongoDB collections.
    - Easy integration with Spring's dependency injection and configuration.
    - Query methods and custom MongoDB queries for collections.

---

## Query Method DSL

**Query Method DSL** (Domain-Specific Language) allows you to define queries by naming methods in repository interfaces. Spring Data automatically converts these method names into queries, providing a seamless way to interact with databases.

### Key Features:
- Simplifies query creation by avoiding explicit SQL or JPQL.
- Uses method naming conventions to generate queries automatically.
- Works for both relational and MongoDB databases.

### Examples:

#### Spring Data JPA:
```
public interface UserRepository extends JpaRepository<User, Long> {  
    List<User> findByLastName(String lastName);  
    List<User> findByAgeGreaterThan(int age);  
}
```

#### Spring Data MongoDB:
```
public interface UserRepository extends MongoRepository<User, String> {  
    List<User> findByFirstName(String firstName);  
    List<User> findByCity(String city);  
}
```

---

## Criteria API

**Criteria API** provides a programmatic way to create dynamic and complex queries. This approach is ideal when query conditions are not known at compile time.

### Key Features:
- Offers fine-grained control over query construction.
- Suitable for dynamic and complex queries.
- Supported in both JPA and MongoDB with slight differences.

### Examples:

#### Spring Data JPA:
```
CriteriaBuilder cb = entityManager.getCriteriaBuilder();  
CriteriaQuery<User> query = cb.createQuery(User.class);  
Root<User> user = query.from(User.class);  
query.select(user).where(cb.equal(user.get("lastName"), "Smith"));  
List<User> result = entityManager.createQuery(query).getResultList();  

```

#### Spring Data MongoDB:
```
Query query = new Query();  
query.addCriteria(Criteria.where("age").gte(25));  
List<User> users = mongoTemplate.find(query, User.class);  
```