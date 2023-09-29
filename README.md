# top-50-tools-and-libs
Curated list of tools and libs for software engineering. 

The list containes development, build and security tools, and libraries for different uses cases.
Tools and libs are mosty for Java but some are more generic.

Version: 1.1.0

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
Static code analyser. Find code smells and security issues. Works on Java, Kotlin, Scala, TypeScript/JavaScript and more.
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

#### NVD Tools
Check your third party libs and OTS software for known vulnerabilities in the NVD feeds. For instance version 8 of MySQL or Java 17.
https://github.com/facebookincubator/nvdtools.

One alternative to this is to find the corresponding Docker image for say MySQL version 8 and scan the image with Trivy. But NVD Tools checks directly in the NIST NVD database so it will be faster.

### AWS Cloudformation
#### Static code analysers for IaC and specifically Cloudformation templates; Checkov and cfn-lint
Checks for insecure infrastructure like encryption that isn't enabled and security group rules that are too permissive.
* https://github.com/aws-cloudformation/cfn-lint
* https://www.checkov.io - can check Terraform/ARM/Biceps/Docker/Kubernetes too. And you can synthezie a stack from CDK and check it.
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
Logging of http requests. Works well with Spring but you need to create some additional classes. Doesn't seesm to work with Micronaut due to the Netty integration.
https://github.com/zalando/logbook

### Spring Boot
Web app framwork for microservices. https://spring.io
* Spring data - Layer on top of JPA
* Spring data projections -  Generate DTOs directly from the SQL query and a DTO class.

### Micronaut
Like Spring Boot but doesn't use reflection so the slow start you can get in Spring Boot will not be there.
https://micronaut.io. It also has support for the repository pattern in Micronaut-data.

### NestJS
Like Spring boot but for Node.js backends in TypeScript. https://nestjs.com. REST controllers look very simlar the corresponding in Spring boot and it has a repository layer (via TypeORM) similar to Spring-data and you will also use dependecy injection.

### Mapstruct
Mapping between DTOs and entities. Uses annotation processing and integrates nicly with Spring/Micronaut and Microprofile/CDI. https://mapstruct.org

### DeltaSpike
In case your stuck with a platform without decent repository layer then use Apache DeltaSpike https://deltaspike.apache.org. Very similar to Spring-data and Quarkus' Panache. It is a layer on top of JPA so it works with both Hibernate and EclipseLink. But it is a bit outdated alas. Check out my [demo project](https://github.com/Lucas3oo/demo-hello-world-open-liberty) that uses DeltaSpike. 

### TSID (Time-Sorted Unique Identifiers) 
Generate TSID for your primary keys in the DB instead of integer or UUID/GUID or [ULID](https://github.com/ulid/spec). TSID is more compact compared to UUID/ULID but otherwise gives the same benefits as ULID (i.e. better DB performance).
* https://github.com/vladmihalcea/hypersistence-tsid
* Hibernate support: https://github.com/vladmihalcea/hypersistence-utils
* My blog post about TSID: https://www.linkedin.com/pulse/primary-keys-db-what-use-id-vs-uuid-something-else-lucas-persson/

### Debezium
Distributed platform for change data capture and outbox pattern. E.g. write once to DB to update a record and propagate an update event to Kafak. But it works with AWS Kinesis too with some extra work. Most DBs are supported like MySQL, PostgreSQL etc.
* https://debezium.io
* Debezium for MySQL: https://debezium.io/documentation/reference/2.1/connectors/mysql.html
* Debezium for AWS Kinesis: https://debezium.io/blog/2018/08/30/streaming-mysql-data-changes-into-kinesis/

### Redis
Cache which also has pub/sub. Integrates directly into Spring as a cache or as a HTTP session store. https://redis.io

### ELK stack
Search and visualize your log streams in a jiffy with ELK.
* ElasticSearch, Kibana, Logstash - https://www.elastic.co/what-is/elk-stack

### AWS Parameter Store
Read the config properties from a central location instead of having ENV-vars or configuration files. Works with e.g. Spring Boot. Particulary useful when you run Spring in as a contiainer and you need to have configuration externalized. You can chose to save values encrypted in the store.
* https://docs.aws.amazon.com/systems-manager/latest/userguide/parameter-store-working-with.html
* Spring cloud AWS and Parameter store: https://docs.spring.io/spring-cloud-aws/docs/2.2.3.RELEASE/reference/html/#integrating-your-spring-cloud-application-with-the-aws-parameter-store

### Azure App Configuration
Same as AWS Parameter Store but for Azure. Has support for Spring. In fact it seems Microsoft does all the Azure-Spring integration libs themself as compared to the AWS support in Spring which is community driven. https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview

If you want secrests in App Configuration to be encrypted then you need to stored them in Azure Key Vault and put a "key vault reference" in the App Configuration. From the application (e.g. Spring) point of view it will be transparent except you need extra permissions assigned to the app for this to work.

### AWS X-Ray
Distributed tracing framwork for your app to see how the app is interacting with AWS services and other custom services.
* Blog post: https://houseofclouds.se/increase-observability-for-your-application-using-aws-x-ray/
* https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html

### Docker/Podman and Docker compose and kind for Kubernetes
* https://podman.io and https://podman-desktop.io
* https://www.docker.com
* https://kind.sigs.k8s.io (manage Kubernetes clusters locally using Docker)
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

AWS S3 proxy which also emulates Azure storage accounts and other "flavours". https://github.com/gaul/s3proxy

Run Lambdas locally: https://github.com/mLupine/docker-lambda

### AWS serverless
* https://aws.amazon.com/serverless/sam/ - AWS serverless application model
* https://serverlessland.com - design patterns and sample code
* https://sst.dev - development kit, fullstack app tooling, framework and deploymet support.
* https://awslabs.github.io/aws-lambda-powertools-typescript/ - support libs for AWS serverless

## Design patterns/frameworks
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
* "Standard" for versioning: Semantic Versioning 2.0.0 - https://semver.org
* "Standard" for change logs -  https://keepachangelog.com
* Comments in code - https://stackoverflow.blog/2021/12/23/best-practices-for-writing-code-comments/
* A collection of full-stack resources for programmers - https://github.com/charlax/professional-programming (this one will keep you busy for weeks)
* https://github.com/kamranahmedse/developer-roadmap
