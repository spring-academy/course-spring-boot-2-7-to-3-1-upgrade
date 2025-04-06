Now that we've commented-out all hard-coded Spring dependency versions in our `pom.xml`, let's continue with **SCAR**.

1. **C**ompile the code.

   We've made our small change, but does it compile?

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.557 s
   [INFO] Finished at: 2023-10-02T18:17:21-06:00
   [INFO] ------------------------------------------------------------------------
   ...
   ```

   It does!

   Let's **A**ssess the change in more detail.

1. **A**ssess the `<version>` change.

   Run the `dependency:tree` goal again and note how the output changed.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep spring-data-jdbc
   ```

   You'll see output that looks like this:

   ```shell
   [INFO] +- org.springframework.data:spring-data-jdbc:jar:3.1.3:compile
   ```

   That's better! The version is now `3.1.3` instead of `2.4.14`

   The Spring Boot Parent is now managing that dependency for us, and it should remain up to date with whatever version the parent deems necessary to include that dependency.

   Thanks, Spring Boot Parent!
