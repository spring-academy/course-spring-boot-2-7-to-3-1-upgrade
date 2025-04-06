We removed the explicit `version` for `assertj`.

What will happen if we remove `assertj` _entirely?_

1. Make a **S**mall change, take 2.

   Open `pom.xml` and **_delete completely_** the `assertj` dependency.

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "assertj-core"
   ```

   ```xml
   <!-- DELETE this entire dependency!  -->
   <!-- <dependency> -->
       <!-- <groupId>org.assertj</groupId> -->
       <!-- <artifactId>assertj-core</artifactId> -->
       <!-- <scope>test</scope> -->
   <!-- </dependency> -->
   ```

   So, what did this do to our project?

1. Check the dependency tree.

   You can now check the Maven Dependency tree output to verify `assertj-core` is still present.

   **NOTE:** In this case we're not trying to limit the output, we want to see the whole tree.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree
   ```

   Search the output for the section `org.springframework.boot:spring-boot-starter-test:jar:2.7.14:test`.

   It shows all the transitive dependencies managed by the `spring-boot-starter-test` dependency.

   ```shell
   [INFO] \- org.springframework.boot:spring-boot-starter-test:jar:3.1.3:test
   [INFO]    +- org.springframework.boot:spring-boot-test:jar:3.1.3:test
   [INFO]    +- org.springframework.boot:spring-boot-test-autoconfigure:jar:3.1.3:test
   [INFO]    +- com.jayway.jsonpath:json-path:jar:2.8.0:test
   [INFO]    +- jakarta.xml.bind:jakarta.xml.bind-api:jar:4.0.0:test
   [INFO]    |  \- jakarta.activation:jakarta.activation-api:jar:2.1.2:test
   [INFO]    +- net.minidev:json-smart:jar:2.4.11:test
   [INFO]    |  \- net.minidev:accessors-smart:jar:2.4.11:test
   [INFO]    |     \- org.ow2.asm:asm:jar:9.3:test
   [INFO]    +- org.assertj:assertj-core:jar:3.24.2:test
   ...
   ```

   As you can see, `assertj-core` is a direct descendent of the `spring-boot-starter-test` dependency.

As long as everything compiles, we don't need to maintain `assertj` at all.
