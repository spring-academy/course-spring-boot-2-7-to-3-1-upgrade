We've made our **S**mall Change. Now let's **C**ompile and **A**ssess!

## **C**ompile the code

Now **C**ompile the code, but as we discussed in the lesson we're going to skip running the tests for now. Don't worry, we'll have a whole set of lessons and labs dedicated to addressing any testing issues we might introduce.

Open the **Terminal** and compile, skipping the tests:

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw clean compile
```

So, what happened?

## **A**ssess the results

Now we can answer the same questions outlined in the first lab:

> Did our code compile?

**_YES!_**

If we had not taken the time to make the Spring Security Changes you would have seen output like the below:

```shell
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR :
[INFO] -------------------------------------------------------------
[ERROR] .../src/main/java/example/cashcard/SecurityConfig.java:[6,72] cannot find symbol
  symbol:   class WebSecurityConfigurerAdapter
  location: package org.springframework.security.config.annotation.web.configuration
[ERROR] .../src/main/java/example/cashcard/SecurityConfig.java:[18,37] cannot find symbol
  symbol: class WebSecurityConfigurerAdapter
[INFO] 2 errors
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.751 s
[INFO] Finished at: 2023-09-21T14:31:06-06:00
[INFO] ------------------------------------------------------------------------
```

Nice! Aren't you glad we took those preparatory steps to ensure this goes smoothly?
