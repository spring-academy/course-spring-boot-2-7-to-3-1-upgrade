Prior to attempting any upgrade it's important to review the release notes for your current version of Spring Boot (in this case 2.7) , its predecessor minor version (2.6), the target version (3.1), and any versions in between. The release notes will familiarize you with deprecations, known issues, and what's new.

## Deprecations

For the purposes of this course you'll definitely want to understand the deprecations for 2.6 and 2.7 because you'll need to address those in order to successfully upgrade to 3.1. The Spring Boot team will maintain deprecations for one (1) minor version only. So, 2.4 deprecations are no longer supported in 2.6, and 2.5 deprecations will no longer be supported in 2.7

- [2.6 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.6-Release-Notes)
- [2.7 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.7-Release-Notes)
- [3.0 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Release-Notes)
- [3.1 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.1-Release-Notes)

## `major` Version Upgrades

It is also important to understand the significance of a `major` version upgrade. A major version upgrade is represented by the "major" number incrementing. For example, "1.0" to 2.0", "10.9.8" to "11.2.5", etc.

Why is this so important when upgrading? According to [semantic versioning](https://semver.org/) (semver) conventions, API developers are allowed to make non-backwards-compatible or "breaking" changes when crossing a major-version boundary.

For a Spring Boot upgrade, deprecations will not be maintained across major version releases for any Spring or Spring Boot library. That means what might have been deprecation warnings in a minor release might turn into compilation or runtime errors when the Spring or Spring Boot teams publish a major release.

### Spring Security

As is the case in most Spring Boot upgrades, Spring Security is of particular concern, so much so that we will upgrade the Spring Security version from 5 to 6 in the hands-on labs as part of our Spring Boot 3.1 upgrade. That means that we'll upgrade the major version of not only Spring Boot, but also the major version of at least one Spring project used within our sample Spring Boot application.

### Review the Docs

With that in mind we recommended you perform some extra due diligence during `major` upgrades. For this upgrade that means reviewing the following in addition to the normal release notes.

- [Upgrading Spring Boot 2.7 to 3.0](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Release-Notes#upgrading-from-spring-boot-27)
- [Upgrading Spring Boot 3.0 to 3.1](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.1-Release-Notes#upgrading-from-spring-boot-30)
- [Spring 3.0 Migration Guide](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Migration-Guide)
- [Spring Security Preparing for 6.0 Guide](https://docs.spring.io/spring-security/reference/5.8/migration/index.html)

As part of the next step in the upgrade process -- "Assess" -- we are going to execute some `preparatory` changes to our code to ensure it is ready for the leap of a `major` release upgrade. Doing that will pay huge dividends as we perform the upgrade.
