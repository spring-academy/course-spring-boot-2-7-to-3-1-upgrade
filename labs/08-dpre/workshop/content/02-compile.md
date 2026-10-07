Actually, at this point, we're _not_ going to **C**ompile the code directly.

Rather, we're going to use the Spring Boot Maven Plugin to start the application!

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw spring-boot:run
```

The application should be up and running, but you'll find some interesting output at the end of the log.

```shell
...
2023-10-03T14:35:21.533-06:00  INFO 74314 --- [           main] example.cashcard.CashCardApplication     : Started CashCardApplication in 4.556 seconds (process running for 4.812)
2023-10-03T14:35:21.535-06:00  WARN 74314 --- [           main] o.s.b.c.p.m.PropertiesMigrationListener  :
The use of configuration keys that have been renamed was found in the environment:

Property source 'Config resource 'class path resource [application.yml]' via location 'optional:classpath:/'':
        Key: spring.kafka.streams.cache-max-size-buffering
                Line: 22
                Replacement: spring.kafka.streams.state-store-cache-max-size


Each configuration key has been temporarily mapped to its replacement for your convenience. To silence this warning, please update your configuration to use the new keys.
```

Interesting! We have at least one property that needs to be migrated.

Let's keep track of this.
