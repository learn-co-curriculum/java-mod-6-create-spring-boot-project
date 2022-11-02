# Create a Spring Boot Project

## Learning Goals

- Create a Spring Boot project using the Spring Initializr.
- Explain the Spring Boot directory structure.

## Introduction

Spring Boot makes it easy to create a project with the required dependencies. We
can use the [Spring Initializr](https://start.spring.io/) tool to generate a
Spring Boot project. We will generate a project in this section and then walk
through some main configurations in the project.

## Generate a Project on Spring Initializr

The [Spring Initializr](https://start.spring.io/) allows us to select the
desired language, build tool, and dependencies and then packages everything
together into a Spring Boot project.

Here are the steps for creating and opening a project:

1. Go to [https://start.spring.io/](https://start.spring.io/).
2. Select the project properties.
   1. Select "Maven Project", as we will use Maven as the build tool.
   2. Select "Java" as the language.
   3. Select the most recent release version of Spring Boot 2. (Make sure it does
      not have "SNAPSHOT" listed after it.)
   4. Select the appropriate Java JDK version.
3. Add dependencies.
   1. Let's add the Spring Data JPA dependency to show how to add dependencies.
   2. Click "ADD DEPENDENCIES".
   3. Search for "spring data jpa".
   4. Select "Spring Data JPA" from the list.
4. Click on the “Generate” button on the bottom. This will download a zip file
   containing the Spring Boot project.
5. Unzip the archive and open it in a preferred code editor or IDE.

![Spring Initializr home screen](https://curriculum-content.s3.amazonaws.com/spring-mod-1/create-spring-boot-project/spring-initializr.png)

## Explore Spring Boot Project

When we open up the Spring Boot project, we'll notice the directory structure
looks like this:

```text
└── /demo
 ├── src
 │   ├── main
 │   │   ├── java
 │   │   ├──── org.example.demo
 │   │   ├────── DemoApplication.java 
 │   │   ├── resources
 │   │   └──── application.properties
 │   └── test
 │       ├── java
 │       └── resources
 └── pom.xml
```

Notice how this looks very similar to a typical Maven project structure. Let's
delve into some of this a little deeper. We'll take a peek at the default class
that Spring Boot has created for us, a second look at the pom.xml file, and then
glance at the application.properties file.

### The Default Class

A Spring Boot project has a single `.java` file that is the entry to the
application. In our case, we will have a `DemoApplication` class. This is what
our `DemoApplication` class looks like:

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
    
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }

}
```

The `@SpringBootApplication` indicates the main class of the SpringBoot
application and this `main` method is the initial entry point of the
application.

### POM Parent

The `pom.xml` file has a `<parent>` section that looks like this:

```xml
<parent>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-parent</artifactId>
   <version>2.7.5</version>
   <relativePath/> <!-- lookup parent from repository -->
</parent>
```

This provides the compatible versions for the dependencies added to the project
which is why most we don’t have to define the version for most of the
dependencies added to the project. It is recommended to let Spring Boot manage
the dependencies.

### Dependencies

Spring Boot provides starter dependencies which package all the required
dependencies for certain tasks. For example, we added the
`spring-boot-starter-data-jpa` dependency which provides everything we need to
work with JPA and an external data source. This is what the `dependencies` looks
like:

```xml
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

### Maven Plugin

The Maven plugin helps set up some default configuration for the project. This
plugin allows us to package executable jar or war archives, run Spring Boot
applications, and generate build information. To learn more about the Maven
plugin, please see the documentation
[here](https://docs.spring.io/spring-boot/docs/current/maven-plugin/reference/htmlsingle/).

```xml
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```

### Properties File

There is an application.properties file in the `resources` directory. This is
where we can add configurations for dependencies or for overriding default
Spring Boot configurations. We'll learn more about the application.properties
file in a later lesson.

## Running the Spring Boot Application

If we were to run our Spring Boot application, we'd go back to the default class
and click on the green play button next to the `main` method:

![Run Demo Application](https://curriculum-content.s3.amazonaws.com/spring-mod-1/create-spring-boot-project/run-spring-boot-application.png)

Since the Spring Initializr only provided us with a base template to creating a
Spring Boot project, when we run the application, it will immediately start and
then finish executing.

In the rest of this module, we will expand upon our Spring Boot application to
be a little more useful.

## Conclusion

We have learned how to set up a Spring Boot project. In the next lessons, we
will create Spring Boot projects with different dependencies but the initial
process of generating a project will be very similar.

## References

- [Spring Initializr](https://start.spring.io/)
- [Spring Boot Maven Plugin Documentation](https://docs.spring.io/spring-boot/docs/current/maven-plugin/reference/htmlsingle/)