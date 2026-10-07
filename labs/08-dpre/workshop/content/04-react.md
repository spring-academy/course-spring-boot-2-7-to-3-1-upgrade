Now, we can fix the offending property.

Replace the key `spring.kafka.streams.cache-max-size-buffering` with the key `spring.kafka.streams.state-store-cache-max-size` as the Migrator suggested:

```editor:select-matching-text
file: ~/exercises/src/main/resources/application.yml
text: "mvc:"
```

Pay attention, as you may not need the whole file in the sample below. The `application.yml` may already have other Spring configurations.

```yaml
spring:
  kafka:
    streams:
      state-store-cache-max-size: 100
```

You can now re-run the application and verify you've eliminated the deprecated key.

Kill any running apps in the **Terminal** by pressing `CTRL-C`, then run the application again.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw spring-boot:run
...
2023-10-03T14:39:30.321-06:00  INFO 75685 --- [           main] example.cashcard.CashCardApplication     : Started CashCardApplication in 4.173 seconds (process running for 4.412)
```

Great! You've eliminated the deprecated properties.

Let's update our upgrade notes again:

```markdown
- Property `spring.kafka.streams.cache-max-size-buffering` is deprecated
  - replaced by `spring.kafka.streams.state-store-cache-max-size`
```
