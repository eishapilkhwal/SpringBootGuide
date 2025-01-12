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

