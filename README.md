Spring Boot Library Sample
============
A library created for educational purposes that includes a service returning a pre-configured message.

Usage
------------
Add the following to your application config:
~~~yml
service:
  message: "YOUR_MESSAGE"
~~~

Use it in the code:
~~~java
@RestController
public class MyController {

    private final MyService myService;

    public MyController(MyService myService) {
        this.myService = myService;
    }

    @GetMapping("/public")
    public String index() {
        return this.myService.message();
    }
}
~~~

Library Deployment
------------
Add the following config to the .m2/settings.xml file:
~~~xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 https://maven.apache.org/xsd/settings-1.0.0.xsd">

    <profiles>
        <profile>
            <id>github</id>
            <repositories>
                <repository>
                    <id>central</id>
                    <url>https://repo1.maven.org/maven2</url>
                </repository>
                <repository>
                    <id>github</id>
                    <url>https://maven.pkg.github.com/allejik/spring-boot-library-sample</url>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
            </repositories>
        </profile>
    </profiles>

    <servers>
        <server>
            <id>github</id>
            <username>YOUR_GITHUB_REPO_USERNAME</username>
            <password>YOUR_CLASSIC_TOKEN_VALUE</password>
        </server>
    </servers>
</settings>
~~~

Execute the following command in the project root:
~~~bash
mvn deploy
~~~
