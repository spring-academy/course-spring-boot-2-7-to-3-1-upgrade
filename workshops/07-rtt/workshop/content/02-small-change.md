Open `pom.xml` and find the `assertj-core` dependency.

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "assertj-core"
```

```xml
<dependency>
    <groupId>org.assertj</groupId>
    <artifactId>assertj-core</artifactId>
    <version>3.24.2</version>
    <scope>test</scope>
</dependency>
```

You'll notice the version of `assertj-core` has been explicitly included. Spring Boot, specifically, the `spring-boot-starter-test` dependency, will manage the version of this library for you.

While we're at it, check the version of `assertj-core` with the Maven Dependency Tree plugin:

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep assertj-core
```

You should see the following output:

```shell
[INFO] \- org.assertj:assertj-core:jar:3.24.2:test
```

Now that we know what's going on, let's deal with this hard-coded test dependency.

1. Make a **S**mall Change

   You can now comment out line the `version` for `assertj` in the `pom.xml`.

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "assertj-core"
   ```

   ```xml
   <dependency>
       <groupId>org.assertj</groupId>
       <artifactId>assertj-core</artifactId>
       <!-- <version>3.24.2</version> -->
       <scope>test</scope>
   </dependency>
   ```

1. Check the dependency tree again.

   Now, check the version of `assertj-core` with the Maven Dependency Tree plugin again:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep assertj-core
   ```

   You should see the following output:

   ```shell
   [INFO] \- org.assertj:assertj-core:jar:3.24.2:test
   ```

   Hmm, the output is the same! It seems like we no longer need the override.

   But why is this?

### Learning Moment: Overrides

Sometimes version overrides are no longer required after an upgrade.

In our scenario, at some point, someone added this version override for `assertj` and now Spring Boot has been updated to use the _same version_.

For example, an issue in the `assertj` library might have been fixed and the Family Cash Card application maintainer needed the newer, fixed version, before Spring Boot was updated to incorporate it.

Now that we have upgraded to Spring Boot 3.1, the `assertj` version managed by the Spring framework is the _same or newer_ than the version the maintainer used.

Because we ended up with the same exact version we know there aren't any impacts to our code! So, while we could compile and assess there is no need in this case. But, we should `react` and update our notes.
