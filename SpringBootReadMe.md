# Learning SpringBoot

**Playlist:** [Spring Boot Playlist](https://youtube.com/playlist?list=PLA3GkZPtsafacdBLdd3p1DyRd5FGfr3Ue&si=iYfT_o7np-xORLFr)

---

## What is Spring Boot?
- **Spring Boot** is a framework for building applications in Java.
- Simplifies the creation of standalone, production-grade, Spring-based applications.
- Applications can be executed directly without the need for external servers.

---

## Tools and Key Concepts

### Maven
- A build automation tool.
- Manages dependencies for the project.
- Converts the project into a `.jar` file.

### JAR (Java Application Archive)
- A package that contains Java classes and associated resources.
- Self-contained and executable.

### WAR (Web Application Archive)
- A package for web applications.
- Needs deployment on an external web server.

---

## Project Structure

1. **`.idea`**: Stores IntelliJ IDE-related configuration files.
2. **`.mvn`**: Maven wrapper folder for managing dependencies and builds.
3. **`.gitignore`**: Specifies files and directories to exclude from version control in Git.
4. **`pom.xml`**: Project Object Model file. Contains project metadata, dependencies, and build configurations.
5. **`src` Folder**:
    - **`main`**: Core application functionality.
        - **`java`**: Contains source code.
        - **`resources`**: Holds configuration files (e.g., database settings).
    - **`test`**: Contains tests for the main application.

---

## JAR File Types

1. **`.jar` FAT JAR**
    - Contains both the compiled code and its dependencies.
    - Self-contained and ready to execute.

2. **`.jar.original`**
    - Contains only the compiled code.

---

## Repackaging Process

- **Command:** `mvn package`
- **Process:**
    1. Generates a `.jar.original` file with just the compiled code.
    2. The installed Maven plugin picks up the `.jar.original`.
    3. Combines it with dependencies to create the final `.jar` file i.e., FAT jar file.

---
## IOC Container

- **Inversion of Control (IOC)** is a design principle where the control of object creation and dependency management is delegated to the container, rather than being handled manually by developers.
- In Spring, the **IOC Container**:
    - Automatically creates objects (called beans).
    - Manages their lifecycle and dependencies.
    - Scans the specified package (e.g., `com.xyz.pyq`) for classes annotated with `@Component`.
    - Registers these classes as beans and provides their instances wherever needed.

---

## Annotations

- **Annotations** are metadata in Java that provide instructions to the compiler or runtime environment.
- They are identified by the `@` symbol and perform specific tasks or define behaviors.
- Example: `@Component` annotation in Spring marks a class as a **Spring Bean**.

---

## @Component

- The `@Component` annotation in Spring is used to register a class as a **Spring Bean**.
- Key Features:
    - Automatically detected during classpath scanning.
    - Registers the class in the IOC Container.
    - Eliminates the need for manual object creation, as the IOC Container provides the required instance.

---

## Bean

- A **Bean** is an object managed by the Spring IOC Container.
- When a class is annotated with `@Component`:
    - The IOC Container creates an instance (bean) of the class.
    - The bean is stored in the IOC Container.
    - Developers can directly use this bean without explicitly initializing it, enabling **dependency injection**.

---

## Application Context

- **ApplicationContext** is the central interface in Spring for interacting with the IOC Container.
- Key Responsibilities:
    - Provides access to beans managed by the IOC Container.
    - Manages the lifecycle of beans (initialization, destruction, etc.).
    - Supports advanced features like:
        - **Internationalization**: For resolving messages based on locale.
        - **Event Propagation**: For publishing and listening to application events.
        - **Resource Loading**: For accessing files and other resources.

---

## @SpringBootApplication

- **@SpringBootApplication** is a primary annotation used in every Spring Boot project, placed over the `main` method's class.
- It combines the functionality of three annotations:
    1. **@Configuration**:
        - Used to define configuration classes in Spring.
        - Works with `@Bean` to create and manage beans.
    2. **@EnableAutoConfiguration**:
        - Enables automatic configuration based on the project's dependencies.
        - Simplifies the setup process for common configurations.
    3. **@ComponentScan**:
        - Scans the specified package for classes annotated with `@Component`, `@Service`, `@Repository`, etc., and registers them in the IOC Container.

---

## @RestController

- Combines the functionality of `@Controller` and `@ResponseBody`.
- Registers the class as a Spring Bean in the IOC Container.
- Automatically maps HTTP requests to methods using annotations like `@GetMapping`, `@PostMapping`, etc.

---

## @Autowired

- **@Autowired** is used for dependency injection in Spring.
- It automatically injects beans into a field, constructor, or setter method.
- Commonly used for **field injection**, where the dependency is directly injected into the variable.

Example:
```java
@Autowired  
private MyService myService;  
```

## @Bean

- **@Bean** is used to define a bean explicitly in a Spring configuration class.
- Written inside a method, not at the class level.
- The method annotated with @Bean returns an object to be managed by the Spring IOC Container.
- Useful when you need fine-grained control over bean creation.

Example
```java
@Configuration  
public class AppConfig {  
    @Bean  
    public MyService myService() {  
        return new MyServiceImpl();  
    }  
}
```
---

# ResponseEntity

- **ResponseEntity** is a class provided by the Spring Framework, commonly used in Spring Boot applications.
- It is used to **customize HTTP responses** sent back to the client.
- You can set the **response status**, **headers**, and **body** using this class.
- It allows you to return different types of data (e.g., JSON, XML, HTML) from controller methods.
- Generics can be used with `ResponseEntity<T>` to specify the type of data being returned.

### Example:
```java
@RestController
public class ExampleController {
    
    @GetMapping("/example")
    public ResponseEntity<String> getExample() {
        return ResponseEntity
                .status(HttpStatus.OK)
                .body("Hello, this is a customized response!");
    }
}
```

---

# Lombok

**Lombok** is a Java library that helps reduce boilerplate code by automatically generating commonly used methods like **getters**, **setters**, **constructors**, and more. It is widely used in Spring Boot applications to simplify class definitions and make the code cleaner and easier to maintain.

---

## Benefits of Using Lombok
- **Reduces Boilerplate Code**: Automatically generates repetitive methods like `getters`, `setters`, etc.
- **Improves Code Readability**: Keeps the focus on business logic rather than verbose code.
- **Saves Development Time**: Eliminates the need for manual code writing for repetitive tasks.

---

## How Lombok Works
- Lombok uses **annotations** to specify what methods should be generated for a class.
- During the **compilation phase**, Lombok scans the annotations and adds the corresponding methods to the **compiled `.class` files**.

---

## Common Lombok Annotations

| **Annotation**        | **Description**                                                                                   |  
|------------------------|---------------------------------------------------------------------------------------------------|  
| `@Getter`             | Generates getter methods for all fields in the class.                                             |  
| `@Setter`             | Generates setter methods for all fields in the class.                                             |  
| `@NoArgsConstructor`  | Generates a no-argument constructor.                                                              |  
| `@AllArgsConstructor` | Generates a constructor with parameters for all fields.                                           |  
| `@ToString`           | Generates a `toString()` method.                                                                  |  
| `@EqualsAndHashCode`  | Generates `equals()` and `hashCode()` methods.                                                    |  
| `@Data`               | Combines `@Getter`, `@Setter`, `@ToString`, `@EqualsAndHashCode`, and `@RequiredArgsConstructor`.  |  
| `@Builder`            | Generates a builder pattern for creating objects.                                                 |  

---

## Example Usage

### Without Lombok
```java
public class User {
    private String name;
    private int age;

    // Getters and Setters
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }

    // Constructor
    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // toString Method
    @Override
    public String toString() {
        return "User{name='" + name + "', age=" + age + "}";
    }
}
```
### With Lombok
```java
import lombok.Data;

@Data
public class User {
    private String name;
    private int age;
}
```
- The @Data annotation automatically generates all the methods (getters, setters, toString, etc.) without writing them manually.
- Lombok annotations do not add methods to the source code but directly to the compiled bytecode.
---

---
[Learning by doing](https://github.com/eishapilkhwal/Memoir)

