Wait, I bet you thought you were done!

In Spring Security 6.0, the Spring Security maintainers decided to remove the `@Configuration` annotation from `@EnableWebSecurity`.

Now is a good time to make sure your security configuration gets picked up when you migrate to Spring Boot 3.1.x.

1. Add the `@Configuration` annotation.

   Update `SecurityConfig` and add the `@Configuration` before the `@EnableWebSecurity` annotation.

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/SecurityConfig.java
   text: "@EnableWebSecurity"
   ```

   ```java
   @Configuration // <== Add this
   @EnableWebSecurity
   public class SecurityConfig { ... }
   ```

   Don't forget to add corresponding import:

   ```java
   import org.springframework.context.annotation.Configuration;
   ```

1. Update our notes.

   Add the following to the `Major Release Considerations` section of the `upgrade-notes.md` file:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   - Add `@Configuration` annotation, which is removed in Spring Security 6.0
   ```

Before we're done, let's establish a new baseline.
