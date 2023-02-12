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
Checks your third party libs (Java and Node) for known vulnerabilities.
http://jeremylong.github.io/DependencyCheck/dependency-check-gradle/index.html
#### SpotBugs
Static code analyser. Find code smells and security issues.
 * https://spotbugs.github.io
 * Security extension: https://find-sec-bugs.github.io
 * Extension: https://github.com/mebigfatguy/fb-contrib
#### Sonarlint
Static code analyser. Find code smells and security issues.
https://plugins.gradle.org/plugin/se.solrike.sonarlint
#### Checkstyle
Static code analyser. More focus on style. E.g. checks for long methods. 
Built into Gradle. https://docs.gradle.org/current/userguide/checkstyle_plugin.html
#### Spotless
Static code analyser. More focus on formatting. Works on Java, TypeScript, C#, Kotlin, Scala you name it.
https://plugins.gradle.org/plugin/com.diffplug.spotless
#### JaCoCo
Code coverage.
Built into Gradle.
* https://docs.gradle.org/current/userguide/jacoco_plugin.html
* Convert to Cobertura format: https://plugins.gradle.org/plugin/com.kageiit.jacobo
#### AWS Cloudformation Gradle plugin
Deploy Cloudformation templates and handle environment properties from Gradle.
https://plugins.gradle.org/plugin/se.solrike.cloudformation

### Security tools
#### OWASP Zap
Web app scanner and DAST (Dynamic Application Security Testing). 
* Blog post about testing a REST API: https://www.linkedin.com/pulse/owasp-zap-easy-way-begin-security-testing-lucas-persson/
* https://www.zaproxy.org
#### Trivy
Scan Docker images for known vulnerabilities.
* Blog post about Trivy: https://www.linkedin.com/pulse/vulnerability-scanning-docker-images-lucas-persson/
* https://aquasecurity.github.io/trivy/v0.37/

### AWS Cloudformation
#### cfn-lint
Linter for Cloudformation templates - https://github.com/aws-cloudformation/cfn-lint
#### cnf_nag
Linter for Cloudformation templates - https://github.com/stelligent/cfn_nag

### DB Tools
#### Flyway
DB schema migration tool. Really a deal breaker! Spring has built in support for Flyway.
With [Testontainers](https://www.testcontainers.org) you can easliy create "unit tests" for your migration scripts.
* https://flywaydb.org
* Gradle plugin: https://plugins.gradle.org/u/flyway

### Openssl
With openssl you can create certificates, check content in p12 files, connect to a web site and check the certificate, and check if a certificate has been revoked.
https://www.openssl.org

## Libs and platforms
### SLF4J and Logback
Java logging framework. 
* https://www.slf4j.org
* https://logback.qos.ch
* Supports MDC (Mapped Diagnostic Context) https://logback.qos.ch/manual/mdc.html
* Format the log record to JSON and send it to the ELK stack, supports MDC: https://github.com/logfellow/logstash-logback-encoder
### Logbook
Logging of http requests.
https://github.com/zalando/logbook

### Spring Boot
Web app framwork for microservices. https://spring.io
* Spring data - Layer on top of JPA
* Spring data projections -  Generate DTOs directly from the SQL query 
### Micronaut
Like Spring Boot but doesn't use reflection so the slow start you can get in Spring Boot will not be there.
https://micronaut.io

### Debezium
Distributed platform for change data capture. E.g. write once to DB to update a record and propagate an update event to Kafak. But it works with AWS Kinesis to with some extra work.
* https://debezium.io
* Debezium for MySQL: https://debezium.io/documentation/reference/2.1/connectors/mysql.html
* Debezium for AWS Kinesis: https://debezium.io/blog/2018/08/30/streaming-mysql-data-changes-into-kinesis/
### Redis
Cache which also has pub/sub. Integrates directly into Spring as a cache or as a HTTP session store. https://redis.io
### ELK stack
Search and visualize your log streams in a jiffy with ELK.
* ElasticSearch, Kibana, Logstash - https://www.elastic.co/what-is/elk-stack

### AWS Parameter Store
Read the config properties from a central location instead oh having ENV-vars or configuration files. Works with e.g. Spring Boot.
* https://docs.aws.amazon.com/systems-manager/latest/userguide/parameter-store-working-with.html
* Spring cloud AWS and Parameter store: https://docs.spring.io/spring-cloud-aws/docs/2.2.3.RELEASE/reference/html/#integrating-your-spring-cloud-application-with-the-aws-parameter-store

### AWS X-Ray
Distributed tracing framwork for your app to see how the app is interacting with AWS services and other custom services.
* Blog post: https://houseofclouds.se/increase-observability-for-your-application-using-aws-x-ray/
* https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html

### Docker/Podman and Docker compose and kind for Kubernetes
* https://podman.io and https://podman-desktop.io
* https://www.docker.com
* https://kind.sigs.k8s.io
* Docker compose Gradle plugin:  https://plugins.gradle.org/plugin/com.avast.gradle.docker-compose

### Unit testing
* Fluent assertions java library - https://assertj.github.io/doc/
* Tasty mocking framework for unit tests in Java - https://site.mockito.org
* Testing asynchronous systems - http://www.awaitility.org
* Mutation testing, how good are your unit test really? - https://pitest.org

### Testcontainers 
Spin up any container inside your "unit tests" like a MySQL or Redis.
https://www.testcontainers.org


## Design patters/frameworks
### Secure coding
* https://www.oracle.com/java/technologies/javase/seccodeguide.html
* https://owasp.org/www-project-top-ten/
* https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf
* https://www.sans.org/top25-software-errors/

### System desing
* The Twelve-factor app - https://12factor.net
* AWS well architected - https://aws.amazon.com/architecture/well-architected

