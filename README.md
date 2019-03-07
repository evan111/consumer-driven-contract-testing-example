****PACT example using Java provider, Java client.****

* I've forked the repo original repo: https://github.com/the-creative-tester/consumer-driven-contract-testing-example

* Original repo documentation: http://the-creative-tester.github.io/Java-Consumer-Driven-Contract-Testing/

****Additions:****

* Pact file generated from Java Client added to git: https://bitbucket.org/skeeka/pact/src/master/dummy-consumer-dummy-provider.json

**Java Client:**

* Test Client and Generate PACT file
```
cd consumer
./gradlew test
```
* File can be found: 
```
../pacts/dummy-consumer-dummy-provider.json
```

* Note the Test Client can be run from your IDE as a JUnit from the Class directly to genreate the PACT file.

* Also see: https://github.com/DiUS/pact-jvm/tree/master/pact-jvm-provider-junit

**Provider**

*Provider Setup and Verification with Maven or Gradle*

1. Run using maven (We would use this as our projects are maven based)

* Launch application and run provider tests against it.
```
cd providerMaven
mvn package && java -jar target/providerMaven-1.0-SNAPSHOT.jar
```
* From another terminal
```
curl http://localhost:8080/hello-world
```
* Verify the provider against PACT file. See gradle plugin readme: https://github.com/DiUS/pact-jvm/tree/master/pact-jvm-provider-maven
```
mvn pact:verify
```

2. Run using gradle
```
cd provider
./gradlew clean build && java -jar build/libs/gs-actuator-service-0.1.0.jar
```
* From another terminal
```
curl http://localhost:8080/hello-world
```
* Verify the provider against PACT file. See gradle plugin readme: https://github.com/DiUS/pact-jvm/tree/master/pact-jvm-provider-gradle
```
./gradlew downloadFile
./gradlew pactVerify
```



