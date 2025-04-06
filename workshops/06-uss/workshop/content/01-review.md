Our version of Spring Security is currently overridden by the property we set in the `pom.xml` `<properties>` section:

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "<properties>"
```

```xml
<properties>
    <java.version>17</java.version>
    <!-- This is the override we added -->
    <spring-security.version>5.8.5</spring-security.version>
    <itextpdf.version>5.5.13.3</itextpdf.version>
</properties>
```

We can verify this with the Maven Dependency Tree plugin:

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep spring-security
[INFO] |  +- org.springframework.security:spring-security-config:jar:5.8.5:compile
[INFO] |  |  \- org.springframework.security:spring-security-core:jar:5.8.5:compile
[INFO] |  |     \- org.springframework.security:spring-security-crypto:jar:5.8.5:compile
[INFO] |  \- org.springframework.security:spring-security-web:jar:5.8.5:compile
```

Notice that the Spring Security Version is set to `5.8.5`.

Now, it's time to upgrade to Spring Security 6. This will can be accomplished by removing the overriding `spring-security.version` property.
