In the previous lab we updated the `spring-boot-starter-parent` to `3.1.3`, and our code is compiling.

But, we need to do some housekeeping to ensure our code and builds aren't stale or fragile. Nobody wants tech debt...right?

So, as a best practice, we'll mitigate any hard-coded Spring dependency versions in our application.

We'll keep using the iterative **SCAR** method as we progressively upgrade our application.

## Make a **S**mall Change

1. Locate hard-coded Spring dependency versions.

   Open `pom.xml` and search through the Spring dependencies within.

   Can you find any hard-coded versions?

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "spring-data-jdbc"
   before: 2
   after: 2
   ```

   Look at `spring-data-jdbc` -- its version is hard-coded!

   ```xml
    <dependency>
       <groupId>org.springframework.data</groupId>
       <artifactId>spring-data-jdbc</artifactId>
       <version>2.4.14</version>
    </dependency>
   ```

2. Search the dependency tree.

   You can also see this version from the Maven Dependency Tree.

   In the **Terminal**, generate the dependency tree with the following command, using the `grep` command to filter for our hard-coded dependency of `spring-data-jdbc`:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep spring-data-jdbc
   ```

   You'll see output that looks like this:

   ```shell
   [INFO] +- org.springframework.data:spring-data-jdbc:jar:2.4.14:compile
   ```

   This version is far too old for the version of Spring Boot we're targeting, which is 3.x.

   Let's try to fix it!

3. Comment out the `<version>` tag.

   Got back to the `pom.xml` and comment-out the hard-coded `spring-data-jdbc` version.

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "spring-data-jdbc"
   before: 2
   after: 2
   ```

   ```xml
    <dependency>
       <groupId>org.springframework.data</groupId>
       <artifactId>spring-data-jdbc</artifactId>
       <!-- comment out the explicit version -->
       <!-- <version>2.4.14</version> -->
    </dependency>
   ```

Ok, time to compile and assess.

