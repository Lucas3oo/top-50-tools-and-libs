# top-50-tools-and-libs
Curated list of tools and libs for software engineering. 

The list containes development, build and security tools, and libraries for different uses cases.
Tools and libs are mosty for Java but some are more generic.

Version: 1.0.0

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

#### AWS S3 Gradle plugin
For instance upload a JAR to an S3 bucket.
https://plugins.gradle.org/plugin/seek.aws

#### Access git from Gradle
https://plugins.gradle.org/plugin/org.ajoberstar.grgit

### Security tools
#### OWASP Zap
Web app scanner and DAST (Dynamic Application Security Testing). 
* Blog post about testing a REST API: https://www.linkedin.com/pulse/owasp-zap-easy-way-begin-security-testing-lucas-persson/
* https://www.zaproxy.org
#### Trivy
Scan Docker images for known vulnerabilities.
* Blog post about Trivy: https://www.linkedin.com/pulse/vulnerability-scanning-docker-images-lucas-persson/
* https://aquasecurity.github.io/trivy/v0.37/

#### NVD Tool
Check your third party libs and OTS software for known vulnerabilities in the NVD feeds. For instance version 8 of MySQL or Java 17.
https://github.com/facebookincubator/nvdtools

### AWS Cloudformation
#### Linters for Cloudformation templates
* https://github.com/aws-cloudformation/cfn-lint
* https://github.com/stelligent/cfn_nag
#### Deploy Cloudformation templates from Gradle
* https://plugins.gradle.org/plugin/se.solrike.cloudformation

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
* Supports MDC (Mapped Diagnostic Context) - https://logback.qos.ch/manual/mdc.html
* Format the log record to JSON and send it to the ELK stack, supports MDC. Works both as logback appender and also useful as an encoder. - https://github.com/logfellow/logstash-logback-encoder
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

### Mapstruct
Mapping between DTOs and entities. Uses annotation processing and integrates nicly with Spring. https://mapstruct.org

### TSID (Time-Sorted Unique Identifiers) 
Generate TSID for your primary keys in the DB instead of integer or UUID/GUID or [ULID](https://github.com/ulid/spec). TSID is more compact compared to UUID/ULID but otherwise gives the same benefits as ULID (i.e. better DB performance). https://github.com/vladmihalcea/hypersistence-tsid and Hibernate support: https://github.com/vladmihalcea/hypersistence-utils

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
Read the config properties from a central location instead of having ENV-vars or configuration files. Works with e.g. Spring Boot. Particulary useful when you run Spring in as a contiainer and you need to have configuration externalized.
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
* AssertJ - Fluent assertions java library, nicer than Hamcrest - https://assertj.github.io/doc/
* Tasty mocking framework for unit tests in Java - https://site.mockito.org
* Testing asynchronous systems - http://www.awaitility.org
* Mutation testing, how good are your unit tests really? - https://pitest.org

### Testcontainers 
Spin up any container inside your "unit tests" like a MySQL or Redis.
https://www.testcontainers.org

### Run AWS locally
Localstack emulate the AWS cloud locally https://localstack.cloud. Some services are free, some not. Basically your start the "localstack" in Docker and you will have to configure/override the AWS endpoints to point to 127.0.0.1 instead. Free services:
* Lambda, API Gateway V1
* S3
* CloudWatch, EventBridge
* Kinesis, DynamoDB, DynamoDB Streams
* KMS, STS
* SES, SNS, SQS

Payed:
* RDS, API Gateway V2, Cognito, ElastiCache, Kinesis, Kinesis Data Analytics
* EKS, ECR, ECS

AWS DynamoDB is possible to run locally without using Localstack: https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html

AWS S3 proxy which also emulates Azure storage accounts and other "flavors". https://github.com/gaul/s3proxy

Run Lambdas locally: https://github.com/mLupine/docker-lambda

## Design patters/frameworks
### Secure coding
* https://www.oracle.com/java/technologies/javase/seccodeguide.html
* https://owasp.org/www-project-top-ten/
* https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf
* https://www.sans.org/top25-software-errors/

### System desing
* https://github.com/donnemartin/system-design-primer
* The Twelve-factor app - https://12factor.net
* AWS well architected - https://aws.amazon.com/architecture/well-architected

### Misc
* Semantic Versioning 2.0.0 - https://semver.org
* Comments in code - https://stackoverflow.blog/2021/12/23/best-practices-for-writing-code-comments/
* A collection of full-stack resources for programmers - https://github.com/charlax/professional-programming (this one will keep you busy for weeks)
* https://github.com/kamranahmedse/developer-roadmap
