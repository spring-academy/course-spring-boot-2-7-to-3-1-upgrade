Let's run through an entire **SCAR** pass to update our Spring Security version.

1. Make a **S**mall Change

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "<properties>"
   ```

   Delete the Spring Security version property:

   ```xml
   <properties>
   	<java.version>17</java.version>
       <!-- Delete the spring-security.version property -->
   	<spring-security.version>5.8.5</spring-security.version>
       <itextpdf.version>5.5.13.3</itextpdf.version>
   </properties>
   ```

   That was truly a **S**mall Change. Let's compile and see the impact.

1. **C**ompile the code

   Now **C**ompile the code. You should see some interesting output.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ...
   [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[24,13] authorizeHttpRequests() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
   [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[27,17] and() in org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer.AuthorizationManagerRequestMatcherRegistry has been deprecated and marked for removal
   [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[28,17] csrf() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.963 s
   [INFO] Finished at: 2023-10-03T08:55:56-06:00
   [INFO] ------------------------------------------------------------------------
   ```

   Ok, what just happened? The code was compiling cleanly before -- no errors or warnings. Now, we have three (3) deprecation messages!

1. **A**ssess the results

   Let's check what happened with the Spring Security version using the dependency tree.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep spring-security
   ```

   You should see the following output:

   ```shell
   [INFO] |  +- org.springframework.security:spring-security-config:jar:6.1.3:compile
   [INFO] |  |  \- org.springframework.security:spring-security-core:jar:6.1.3:compile
   [INFO] |  |     \- org.springframework.security:spring-security-crypto:jar:6.1.3:compile
   [INFO] |  \- org.springframework.security:spring-security-web:jar:6.1.3:compile
   ```

   We see that Spring Boot is now managing the Spring Security version and it is now at `6.1.3`.

   That's a big leap... but we made it so let's deal with those deprecations!

1. **R**eact to the error output

   Let's update our notes.

   Add a new section for the security upgrade `Upgrade Spring Security Version` to our `upgrade-notes.md` file.

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   ### Upgrade Spring Security Version

   - Remove Spring Security version override and upgrade Spring Security to `6.1.3`
   - Spring Security deprecations
     \`\`\`
     [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[24,13] authorizeHttpRequests() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
     [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[27,17] and() in org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer.AuthorizationManagerRequestMatcherRegistry has been deprecated and marked for removal
     [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[28,17] csrf() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
     \`\`\`
   - [Migrating to Spring Security 6](https://docs.spring.io/spring-security/reference/6.0/migration/index.html)
   ```

The **SCAR** method has always been an iterative process. It's an especially iterative process, now - even more so!

Let's move on and address these deprecations!
