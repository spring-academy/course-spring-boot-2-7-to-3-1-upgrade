The `spring-boot-properties-migrator` did its job and found a property that's been deprecated and replaced by another.

Let's note this in `upgrade-notes.md`.

Open the file and add this new section:

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

```markdown
## Address deprecated Spring Properties

- Property `spring.kafka.streams.cache-max-size-buffering` is deprecated
```
