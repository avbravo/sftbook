


```java
<plugins>
    ...
    <plugin>
        <groupId>fish.payara.maven.plugins</groupId>
        <artifactId>payara-micro-maven-plugin</artifactId>
        <version>1.0.5</version>
        <executions>
            <execution>
                <id>package-payara</id>
                <phase>package</phase>
                <goals>
                    <goal>bundle</goal>
                </goals>
            </execution>
            <execution>
                <id>start-payara</id>
                <goals>
                    <goal>start</goal>
                </goals>
            </execution>
            <execution>
                <id>pre-integration-payara</id>
                <phase>pre-integration-test</phase>
                <goals>
                    <goal>start</goal>
                </goals>
                <configuration>
                    <!-- start in the background -->
                    <daemon>true</daemon>
                </configuration>
            </execution>
            <execution>
                <id>post-integration-payara</id>
                <phase>post-integration-test</phase>
                <goals>
                    <goal>stop</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <payaraVersion>5.192</payaraVersion>

            <deployWar>true</deployWar>

            <contextRoot>/</contextRoot>

            <javaCommandLineOptions>
                <!-- Java 9+ options -->
                <option>
                    <key>--add-opens</key>
                    <value>java.base/jdk.internal.loader=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>jdk.management/com.sun.management.internal=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-exports</key>
                    <value>java.base/jdk.internal.ref=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>java.base/java.lang=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>java.base/java.nio=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>java.base/sun.nio.ch=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>java.management/sun.management=ALL-UNNAMED</value>
                </option>
                <option>
                    <key>--add-opens</key>
                    <value>java.base/sun.net.www.protocol.jrt=ALL-UNNAMED</value>
                </option>
            </javaCommandLineOptions>
        </configuration>
    </plugin>
    ...
</plugins>

```

