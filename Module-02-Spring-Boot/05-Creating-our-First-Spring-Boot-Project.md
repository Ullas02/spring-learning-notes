# Creating Your First Spring Boot Project

## 🎯 What is it?

In this lesson, you'll create your first Spring Boot project using IntelliJ IDEA.

Rather than simply generating a project, we'll understand what each option means and why it matters.

---

## ❓ Why do we need it?

A Spring Boot project contains much more than Java source code. It includes:

- Dependency management
- Build configuration
- Application configuration
- Resource files
- Test structure

Understanding the generated project structure will make it easier to navigate and maintain real-world applications.

---

## ⚙️ Step 1: Create the Project

Open **IntelliJ IDEA**.

Select:

```
File
    → New
        → Project
```

Choose:

```
Spring Initializr
```

Fill in the details:

| Field | Value |
|--------|-------|
| Name | spring-boot-day-01-first-project |
| Group | com.example |
| Artifact | spring-boot-day-01-first-project |
| Package | com.example.demo |
| Language | Java |
| Build Tool | Maven |
| JDK | 21 (or your installed LTS version) |
| Packaging | Jar |

Click **Next**.

---

## ⚙️ Step 2: Select Dependencies

Add only:

- Spring Web

That's it.

Avoid adding unnecessary dependencies at the beginning. Start with the minimum required and add more as the application grows.

---

## ⚙️ Step 3: Finish the Project

Click **Finish**.

IntelliJ IDEA will:

- Generate the project.
- Download Maven dependencies.
- Index the project.

The first build may take a few minutes depending on your internet connection.

---

## ⚙️ Step 4: Project Structure

A typical Maven-based Spring Boot project looks like:

```
spring-boot-day-01-first-project/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   └── resources/
│   │
│   └── test/
│
├── pom.xml
├── .gitignore
├── mvnw
├── mvnw.cmd
└── README.md
```

---

## ⚙️ Understanding Each Folder

### `src/main/java`

Contains the application's Java source code.

You'll create:

- Controllers
- Services
- Repositories
- Configuration classes
- Models

Most of your development happens here.

---

### `src/main/resources`

Contains non-Java resources such as:

- `application.properties`
- Static resources
- Templates
- Configuration files

---

### `src/test`

Contains unit and integration tests.

Keeping tests separate from production code improves maintainability and code quality.

---

### `pom.xml`

The Maven Project Object Model (POM) file.

It defines:

- Project metadata
- Dependencies
- Plugins
- Build configuration

Whenever you add a new library, you'll usually update this file.

---

### `mvnw` and `mvnw.cmd`

These are the **Maven Wrapper** scripts.

They allow anyone to build the project with the correct Maven version, even if Maven is not installed globally.

---

### `.gitignore`

Specifies which files Git should ignore, such as:

- `target/`
- IDE-specific files
- Temporary build artifacts

This keeps your repository clean.

---

## ⚙️ Step 5: The Main Class

Spring Initializr generates a class similar to:

```java
@SpringBootApplication
public class SpringBootDay01FirstProjectApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootDay01FirstProjectApplication.class, args);
    }

}
```

### Line-by-Line Explanation

#### `@SpringBootApplication`

A convenience annotation that combines several important Spring annotations.

We'll study its internals in a later lesson.

---

#### `public static void main(...)`

The standard Java entry point.

Execution starts here when you run the application.

---

#### `SpringApplication.run(...)`

Bootstraps the Spring Boot application by:

- Creating the Spring IoC container.
- Performing auto-configuration.
- Initializing beans.
- Starting the embedded web server (for web applications).

---

## ⚙️ Step 6: Run the Application

Run the main class.

In the console, look for messages indicating:

- Spring Boot has started.
- Embedded Tomcat has started.
- The application is listening on port `8080`.

If there are no errors, your application is running successfully.

---

## ⚙️ Step 7: Verify the Application

Open a browser and navigate to:

```
http://localhost:8080
```

Since we haven't created any controllers yet, you'll likely receive a **404 Not Found** response.

This is expected. It confirms that:

- The server is running.
- The application is listening for requests.

---

## 💻 Example Project Structure

```
src
├── main
│   ├── java
│   │   └── com/example/demo
│   │       └── SpringBootDay01FirstProjectApplication.java
│   │
│   └── resources
│       └── application.properties
│
└── test
    └── java
```

---

## ✅ Benefits

- Standardized project layout.
- Easy navigation.
- Consistent team collaboration.
- Better maintainability.
- Simple dependency management.
- Ready for production-grade development.

---

## ⚡ Backend Engineer Tips

Avoid adding every dependency "just in case."

Each dependency:

- increases build time,
- increases application size,
- may introduce security vulnerabilities,
- and can create version conflicts.

Add only what your application actually needs.

---

## ❌ Common Mistakes

- Choosing the wrong Java version.
- Adding unnecessary starter dependencies.
- Editing generated files before understanding their purpose.
- Committing the `target/` directory to Git.
- Ignoring Maven download errors during project creation.

---

## 📝 Quick Revision

- Use Spring Initializr to generate the project.
- Add only required dependencies.
- `src/main/java` contains Java code.
- `src/main/resources` contains configuration.
- `pom.xml` manages dependencies and builds.
- `SpringApplication.run()` starts the application.
- A 404 response on `http://localhost:8080` is expected before adding controllers.
