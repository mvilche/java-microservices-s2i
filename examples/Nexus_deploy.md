## Deploy artifact with maven to nexus repository


1 - Add to pom.xml

```console
    <distributionManagement>
        <repository>
            <id>nexus</id>
            <url>http://nexus.local.repo/repository/maven-local/</url>
        </repository>
    </distributionManagement>
    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-deploy-plugin</artifactId>
                    <version>2.8.2</version>
                </plugin>
            </plugins>
        </pluginManagement>
        <plugins>
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>sonar-maven-plugin</artifactId>
                <version>3.2</version>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-deploy-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```

2 - Push artifactory with s2i image

s2i build http://git.repo java-s2i:jdk11 myapp --loglevel=1 -e NEXUS_MIRROR_URL="http://nexus.local.repo/repository/maven-local/" --network host -e NEXUS_SERVER_ID=nexus -e NEXUS_SERVER_USERNAME=admin -e NEXUS_SERVER_PASSWORD=adminadmin -e MVN_OVERRIDE_COMMAND="mvn clean install && mvn deploy"