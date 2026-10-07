Spring Security is one of the most impactful of all the components of the Spring Framework. It is necessarily complex and deserves special attention during an upgrade.

The Spring Security team also has their own distinct process relative to versioning and deprecations. Therefore, we like to treat Spring Security as an "upgrade _within an_ upgrade."

## Reviewing the Prep Phase

Earlier, during the **Prep** phase, we learned about `major` version upgrade considerations and made some changes to help minimize the ripple effect when we jumped from Spring Boot 2.7 to 3.1. To do this, we temporarily pinned our Spring Security version to `5.8.5`.

Now, we need to allow Spring Boot to manage that version, which will bring us to the current supported version at the time of this writing of Spring Security 6.

Because we made a leap across both Spring Boot and Spring Security major release boundaries, and we landed two (2+) minor versions ahead of where we started, we're likely to see some follow-on ripples in the form of deprecations once we remove the Spring Security version override.

Let's run a mini "Upgrade" path, just for Spring Security.

## Prep

1. ## Review the `Migrating to 6 Spring Security Guide`
   - [Migrating to Spring Security 6](https://docs.spring.io/spring-security/reference/6.0/migration/index.html)

## Assess

Review your application source and configuration. Is your application impacted? Are there things you saw in the release notes that you must act upon?

**Hint:** Yes, you're probably impacted!

## Update

Remove the Spring Security version override and compile. Assess the results and work through any issues.

Remember to make changes one at a time, compiling in-between. Follow the **SCAR** technique!

@@@alert
{
"text": "We came into this module with application source code that was compiling successfully, and it is important that we leave this module the same way!",
"type": "warning"
}
@@@

## Test and Release

We'll perform these steps as part of the overall upgrade process.

## Establish A New Baseline

Document the current state in writing and in source control.

1. Take note of any errors, warnings, or issues in the `upgrade-notes.md` file.
   1. Append a new heading to the document titled - "Upgrade Spring Security Version".
   2. Document any remaining warnings, or other known issues.
2. Issue a commit.
