# top-50-tools-and-libs
Curated list of tools and libs for software engineering. 

The list containes development, build and security tools, and libraries different uses cases.
Tools and libs are mosty for Java but some are more generic.

## Tools

### Gradle plugins
#### jib-gradle-plugin
Containerize your Java application.
Gradle plugin to create Docker images without having to write a Dockerfile. The apps dependencies will be in a separate layer to save some space.
https://github.com/GoogleContainerTools/jib/

#### OWASP dependency-check-gradle plugin
Check your third party libs (Java and Node) for known vulnerabilities.
http://jeremylong.github.io/DependencyCheck/dependency-check-gradle/index.html

#### SpotBugs
Static code analyser. Find code smells.
 * https://spotbugs.github.io
 * Security extension: https://find-sec-bugs.github.io
 * Extension: https://github.com/mebigfatguy/fb-contrib
#### Sonarlint
Static code analyser. Find code smells.
https://plugins.gradle.org/plugin/se.solrike.sonarlint

#### Checkstyle
Static code analyser. More focus on style. E.g. not too long methods. 
Built into Gradle.
#### Spotless
Static code analyser. More focus on formatting.
https://plugins.gradle.org/plugin/com.diffplug.spotless
#### JaCoCo
Code coverage.
Built into Gradle.
* Convert to Cobertura format: https://plugins.gradle.org/plugin/com.kageiit.jacobo


#### AWS Cloudformation Gradle plugin
Deploy Cloudformation templates and handle environment properties from Gradle.
https://plugins.gradle.org/plugin/se.solrike.cloudformation

### Security tools
#### OWASP Zap
Web app scanner and DAST (Dynamic Application Security Testing). See my blog post about testing a REST API, https://www.linkedin.com/pulse/owasp-zap-easy-way-begin-security-testing-lucas-persson/.
https://www.zaproxy.org

#### Trivy
Scan Docker images for known vulnerabilities.
https://aquasecurity.github.io/trivy/v0.37/

### AWS Cloudformation
#### cfn-lint
Linter for Cloudformation templates - https://github.com/aws-cloudformation/cfn-lint
#### cnf_nag
Linter for Cloudformation templates - https://github.com/stelligent/cfn_nag

### DB Tools
#### Flyway
DB schema migration tool. Really a deal breaker! Spring has built in support for Flyway.
* https://flywaydb.org
* Gradle plugin: https://plugins.gradle.org/u/flyway

## Libs and platforms
### SLF4J and Logback
Java logging framework. 
* https://www.slf4j.org
* https://logback.qos.ch
* Supports MDC (Mapped Diagnostic Context) https://logback.qos.ch/manual/mdc.html
### Logbook
Logging of http requests.
https://github.com/zalando/logbook

### Spring Boot
Web app framwork for microservices.
* Spring data - Layer on top of JPA
* Spring data projections -  Generate DTOs directly from the SQL query 
### Micronaut
Like Spring Boot but doesn't use reflection.

### Debezium
Distributed platform for change data capture - https://debezium.io
### Redis
Cache which also has pub/sub. Integrates directly into Spring.

### AWS Parameter Store
Read the config properties from a central location instead oh having ENV-vars or configuration files. Works with e.g. Sprign Boot.

### Unit testing
* Fluent assertions java library - https://assertj.github.io/doc/
* Tasty mocking framework for unit tests in Java - https://site.mockito.org
* Testing asynchronous systems - http://www.awaitility.org
* Mutation testing, how good are your unit test really? - https://pitest.org

## Design patters/frameworks
### Secure coding
* https://www.oracle.com/java/technologies/javase/seccodeguide.html
* https://owasp.org/www-project-top-ten/
* https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf
* https://www.sans.org/top25-software-errors/

### System desing
* The Twelve-factor app - https://12factor.net
* AWS well architected - https://aws.amazon.com/architecture/well-architected

