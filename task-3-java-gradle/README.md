# Task 3: Java Application Using Gradle

## Overview
A Java 21 application demonstrating Gradle build automation, dependency management, automated testing, and Jenkins CI/CD integration.

## Technologies
- Java 21
- Gradle 8.14.3
- Groovy DSL
- JUnit Jupiter 5.12.1
- Jenkins

## Project Structure
- `app/src/main/java/` - Application source code
- `app/src/test/java/` - Automated tests
- `app/build.gradle` - Build and dependency configuration
- `gradlew` - Gradle Wrapper
- `Jenkinsfile` - Jenkins pipeline

## Build and Test
```bash
./gradlew clean build
```

## Run Application
```bash
./gradlew run
```

Expected output: `Hello World!`

## Generate JAR
```bash
./gradlew jar
```

The JAR is generated under `app/build/libs/`.

## Jenkins CI/CD
The pipeline builds and tests the application, runs it, and archives the generated JAR as a Jenkins artifact.

## Task Objectives
- Automate Java builds with Gradle.
- Manage dependencies.
- Run automated tests.
- Integrate Jenkins CI/CD.
- Package the application for delivery.
