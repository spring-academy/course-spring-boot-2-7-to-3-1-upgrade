At this point, you've reconfigured Spring Security to set up for the jump to Spring Boot 3.1.x. Now is the time to make sure everything is still working correctly. Go ahead and run the tests.

1. Compile the code.

   If all went as planned, we should no longer have the deprecation warnings we introduced by upgrading Spring Security:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.308 s
   [INFO] Finished at: 2023-08-21T22:02:43Z
   [INFO] ------------------------------------------------------------------------
   ```

1. Run the tests and ensure we have a **_Known Good State_**.

   ```shell
   [~/exercises] $ ./mvnw clean test
   ```

   All the tests should be passing with no `Skipped` tests.

   ```shell
   [INFO] Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
   [INFO]
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  8.531 s
   [INFO] Finished at: 2023-08-10T22:55:28Z
   [INFO] ------------------------------------------------------------------------
   ```

   Nice! We have our new baseline.

1. Update our notes.

   Let's record our result in the `upgrade-notes.md` file.

   Add a line in the `Major Release Considerations` section:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   _Result:_ code compiles without errors or warnings and all tests pass (no skipped tests)!
   ```

We did it! We have completed some important preparatory work that will make the transition to Spring Boot 3.1 much easier!
