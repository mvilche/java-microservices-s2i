# Java Openjdk Quarkus - Wildfly Microservices S2i Images


## RockyLinux - CentOS - Alpine - Fedora - Debian
## Openjdk 16,15,14,13,11,8

![Docker Stars](https://img.shields.io/docker/stars/mvilche/java-microservices-s2i.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/mvilche/java-microservices-s2i.svg)
![Docker Automated](https://img.shields.io/docker/cloud/automated/mvilche/java-microservices-s2i)
![Docker Build](https://img.shields.io/docker/cloud/build/mvilche/java-microservices-s2i)


# Features

- Non-root
- Okd Ready
- Kubernetes Ready
- S2i build images
- S2i runtime images
- Maven
- Gradle
- Jolokia Java monitoring
- Prometheus Java monitoring
- Glowroot Java monitoring
- Support Wildfly Throntail, Wildfly Bootable, Quarkus, custom

### Deploy Environments 


| Environment | Details |
| ------ | ------ |
| TIMEZONE | Set Timezone (America/Montevideo, America/El_salvador) |
| EXTRA_JAVA_OPTS | Add extra options to JAVA_OPTS |
| OVERRIDE_JAVA_OPTS | Override default JAVA_OPTS options |
| APP_OPTIONS | set extra arguments when application start |
| WAITFOR_HOST | set name host |
| WAITFOR_PORT | set port for WAITFOR_HOST |
| JOLOKIA_ENABLE | Enable jolokia jmx monitoring|
| PROMETHEUS_ENABLE | Enable prometheus jmx monitoring |
| GLOWROOT_ENABLE | Enable glowroot jmx monitoring |
| GLOWROOT_CENTRAL_COLLECTOR | Send jmx metrics to Glowroot Central - Example http://collector:8181 |
| GLOWROOT_CENTRAL_COLLECTOR_AGENTID | Agent.id name when send data to Glowroot Central - Example myapp |



### Build Environments 


| Environment | Details |
| ------ | ------ |
| MVN_OPTS | Maven options  |
| MVN_OVERRIDE_COMMAND | Override default mvn command. Default mvn clean package  |
| GRADLE_OPTS | Gradle options  |
| NEXUS_MIRROR_URL | Nexus repository override repository in pom.xml |
| NEXUS_SERVER_PASSWORD | Nexus repository auth password |
| NEXUS_SERVER_USERNAME | Nexus repository auth username |
| NEXUS_SERVER_ID | Nexus repository id name. |
| QUARKUS_PACKAGE_TYPE | Quarkus package type values: fast-jar, uber-Jar |
| RUNTIME_ASSEMBLE_CUSTOM_COMMAND_RUN | Run custom command in assemble-runtime process |
| ARTIFACTORY_NAME | Search for artifcatory with specific name |


### Generate builder image

```console
Example build opendjdk 11 alpine image

 docker build -t java-microservices:jdk11-alpine -f openjdk11/Dockerfile.jdk.alpine contrib

```

### Java application image use s2i

```console

s2i build https://github.com/myuser/java-sample-app.git java-microservices:jdk11-alpine myapp:latest --incremental

```


### Run application

```console

docker run -p 8080:8080 myapp:latest

```

### How use s2i

```console

https://github.com/openshift/source-to-image

```

License
----

Martin vilche
