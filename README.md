# learnvest qa code challenge
This is a small [spring-boot](https://projects.spring.io/spring-boot/) based project that contains a mixture of unit and integration tests within a [maven multi-module](https://maven.apache.org/guides/mini/guide-multiple-modules.html) project.

The project is comprised of the following modules:
```
commons = shared code
integration = simple example integrations to the provided RESTful service
service = example of a simple RESTful service
```

To perform a build and execute all unit tests across all of the modules:
```
mvn clean install
```

To execute all integration tests across all of the modules:
```
mvn -P test-integration test
```

See `learnvest-qa-code-challenge/service/src/main/resources` for available profiles.
By default, application.properties configures an in memory instance of H2 so that anyone can use this project immediately.

To run with default h2 in memory database:
```
cd service
mvn spring-boot:run
```

To run with locally installed MySQL database configured via port 3306 with a schema named `learnvest-qa-code-challenge`
as defined within `learnvest-qa-code-challenge/service/src/main/resources/application-localmysql.properties`:
```
cd service
mvn spring-boot:run -Drun.jvmArguments="-Dspring.profiles.active=localmysql"
```

Once the application is running the REST documentation and tester is available via Swagger via:
```
http://localhost:8080/webjars/swagger-ui/2.1.8-M1/index.html?url=/v2/api-docs/#!/card-rest-controller
```

Want the project to produce an old school WAR (will reside within service/target) that you could deploy to your own container?
```
mvn -P war install
```
