# boot-issue-5491

This is a test application to be used with
[Spring Cloud Config](http://cloud.spring.io/spring-cloud-config/)'s
config server.

This is for the purpose of reproducing Spring Boot
[issue #5491](https://github.com/spring-projects/spring-boot/issues/5491).

See the [config-server repo](https://github.com/shakuzen/config-server)
and the [config-repo](https://github.com/shakuzen/config-repo-5491)
to reproduce the reported issue.

## Reproduction

Check the custom logging configuration to be used: [logback-spring.xml](https://github.com/shakuzen/config-repo-5491/blob/master/logback-spring.xml).

After following the instructions for starting the [config-server](https://github.com/shakuzen/config-server),
clone this repository and follow the steps below.

### Working case

1. With`spring-boot-starter-parent`'s version as `1.3.2.RELEASE`
2. Start the application
3. Verify that the expected log file is output as `target/foo.log`

Note however, the log file pattern is not customized due to Spring Boot [issue 5073](https://github.com/spring-projects/spring-boot/issues/5073).

### Broken case

1. Change `spring-boot-starter-parent` to `1.3.3.RELEASE`
2. Start the application
3. Confirm file `LOG_FILE_IS_UNDEFINED` is output to the root of the project

You may also confirm the application's set System properties from the Actuator `/env` endpoint.

The same results can be achieved with `1.3.4.BUILD-SNAPSHOT`.
