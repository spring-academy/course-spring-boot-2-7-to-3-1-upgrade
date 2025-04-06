Like `http.authorizeHttpRequests` the `csrf` method has been deprecated in favor of the new `Customizer` interface.

We'll use a similar lamba expression, but we'll use the collapsed method syntax.

1. Fix the `crsf()` method call.

   Open `SecurityConfig` again and rewrite the `csrf()` using a lambda that accepts the `Customizer`:

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/SecurityConfig.java
   text: "csrf()"
   ```

   Replace `csrf().disable()` with `csrf(AbstractHttpConfigurer::disable)`

   ```java
   .csrf(AbstractHttpConfigurer::disable)
   ```

   Be sure to add the new import:

   ```java
   import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;
   ```

1. **C**ompile the code

   Now is a good time to **C**ompile the code again.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ```

   Woohoo! We have a clean compile. No more deprecation messages in the output

   ```shell
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.706 s
   [INFO] Finished at: 2023-10-03T09:46:01-06:00
   [INFO] ------------------------------------------------------------------------
   ```

   Success! We're compiling without deprecation warnings again.

1. Update our notes.

   Before we move on, let's note the change in the `upgrade-notes.md` file.

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   - Update `csrf` to use the new customizer interface
   ```

Before we're done, let's establish a new baseline again.
