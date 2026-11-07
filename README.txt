DYNAMIC-MATCHER-DEMO - COMPLETE ECLIPSE PROJECT

Project contents:
- pom.xml: Spring Boot, Spring Cloud Contract and test dependencies/plugins
- src/main/java/com/example/DynamicMatcherDemoApplication.java: application entry point
- src/main/java/com/example/AuthController.java: POST /ms1/signin demonstration endpoint
- src/main/resources/application.properties: app name and port
- src/test/java/com/example/BaseContractTest.java: Spring Cloud Contract base test
- src/test/java/com/example/DynamicMatcherDemoApplicationTests.java: context-load test
- src/test/resources/contracts/signin-contract.yml: POST contract and $.token regex matcher

Requirements:
- JDK 21
- Eclipse with Maven (m2e) support
- Internet connection for Maven to download dependencies

Import into Eclipse:
1. Extract this ZIP file.
2. In Eclipse choose File > Import > Maven > Existing Maven Projects.
3. Browse to the extracted dynamic-matcher-demo folder.
4. Select pom.xml and click Finish.
5. Right-click the project > Maven > Update Project.
6. Confirm Project > Properties > Java Build Path uses JDK 21.

Run the application:
1. Right-click DynamicMatcherDemoApplication.java.
2. Choose Run As > Spring Boot App.
3. POST to http://localhost:8080/ms1/signin with:
   {"username":"testuser","password":"password123"}
4. A JSON response containing a non-empty token string is returned.

Run contract tests:
1. Right-click the project > Run As > Maven build...
2. Enter clean test in Goals.
3. Click Run and inspect the Console for BUILD SUCCESS.

Contract matcher:
- JSONPath $.token selects the token response field.
- Regex .+ accepts any non-empty string.

IMPORTANT LIMITATION:
This is an educational contract-testing demonstration. The controller returns a random UUID string;
it is not a signed JWT, does not validate credentials against a user store, and is not production-ready.
The project does not bundle Maven's downloaded dependency cache; Maven downloads dependencies on first build.
