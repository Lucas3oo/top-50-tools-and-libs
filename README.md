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
Static code analyser
#### Sonarlint
Static code analyser
#### Checkstyle
Static code analyser
#### Spotless
Static code analyser
#### JaCoCo
Code coverage

### OWASP Zap
### Trivy
Scan Docker images for known vulnerabilities.
https://aquasecurity.github.io/trivy/v0.37/

### AWS Cloudformation
#### cfn-lint
Linter for Cloudformation templates - https://github.com/aws-cloudformation/cfn-lint
#### cnf_nag
Linter for Cloudformation templates - https://github.com/stelligent/cfn_nag

## Libs and platforms
### Spring
### Micronaut
### AssertJ
Fluent assertions java library - https://assertj.github.io/doc/
### Mockito
Tasty mocking framework for unit tests in Java - https://site.mockito.org
### Awaitility
Testing asynchronous systems - http://www.awaitility.org
### PIT
Mutation testing, how good are your unit test really? - https://pitest.org
### Debezium
Distributed platform for change data capture - https://debezium.io

## Design patters/frameworks
### Secure coding
https://www.oracle.com/java/technologies/javase/seccodeguide.html

https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf

### System desing
* The Twelve-factor app - https://12factor.net
* AWS well architected - https://aws.amazon.com/architecture/well-architected

