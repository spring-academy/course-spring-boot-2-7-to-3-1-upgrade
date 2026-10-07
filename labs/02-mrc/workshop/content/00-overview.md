The focus of this lab is understanding the potential increased impacts of a `major` release upgrade. In the case of the Spring Boot 2.7 to 3.1 upgrade, a great example of those impacts can be found in Spring Security. Spring Security 6.0, a major version bump, was released to be compatible with Spring Boot 3.

To bridge the gap or make the transition across the `major` release boundary easier, the Spring Security maintainers released an interim 5.8.x release. So, as part of our `prep` for the Spring Boot 3.1 we'll perform a minor upgrade of Spring Security to 5.8.x.

**NOTE:** At the time of this writing, the current Spring Boot 2.7.x version is `2.7.14` and the current Spring Security 5.8.x version is `5.8.5`.

## Review our Upgrade Notes

Before we begin, remember that we're keeping detailed notes of the baseline state of our application as we upgrade it. Take a look at `upgrade-notes.md` to review where we are now.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

