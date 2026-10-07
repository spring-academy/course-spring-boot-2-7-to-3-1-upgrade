The `PasswordEncoder` implementations have been moved to static factories going forward.

One caveat here, is that you'll need to scope these to the major/minor version of Spring Security.

1. Update the usage of `Pbkdf2PasswordEncoder`.

   Replace the `return` statement with the static factory method for Spring Security 5.8

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/SecurityConfig.java
   text: "return new Pbkdf2PasswordEncoder"
   ```

   ```java
   return Pbkdf2PasswordEncoder.defaultsForSpringSecurity_v5_8();
   ```

   **NOTE:** This factory method has the Spring Security major/minor version in the method signature.

1. **C**ompile the code.

   Now is a good time to **C**ompile the code again.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ```

   Success! You've been able to deal with all the Spring Security deprecations... Nice!

   ```shell
   [INFO] Compiling 5 source files to /course-spring-boot-2-7-to-3-1-upgrade-code/target/classes
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   ```

1. Update our notes.

   Before we move on, let's note the change again in the `upgrade-notes.md` file.

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   - Replaced `new Pbkdf2PasswordEncoder` with static factory method for Spring Security 5.8
   ```

No more deprecations! Are we done? Let's find out.
