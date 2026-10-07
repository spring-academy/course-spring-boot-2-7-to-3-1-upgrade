Now that we've commented-out `lombok`'s hard-coded version in our `pom.xml`, let's continue with **SCAR**.

1. **C**ompile the code.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.578 s
   [INFO] Finished at: 2023-10-02T18:30:15-06:00
   [INFO] ------------------------------------------------------------------------
   ...
   ```

   Awesome! Our code still compiles...now let's assess what happened

1. **A**ssess the version change.

   Run the `dependency:tree` goal again and note how the output changed.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep lombok
   ```

   You'll see output that looks like this:

   ```shell
   [INFO] +- org.projectlombok:lombok:jar:1.18.28:compile
   ```

   That's _much_ better. The version is now the newer `1.18.28` rather than the older `1.18.22`.

Lombok is a widely used project and the Spring Maintainers have provided dependency management for it. Thanks for managing that for us, Spring!
