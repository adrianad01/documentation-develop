# Maven Commands

|Comand| Description|
|--------------------------------|------------|
|`mvn -N io.takari:maven:wrapper`|This comand create the `.mvn` directory and the Maven Wrapper files `(mvnw, mvnw.cmd)`|
|`mvn clean`|Deletes the `target/` directory (removes compiled files and build artifacts)|
|`mvn clean install`|Cleans, compiles, runs tests, and installs the `.jar ` or `.war` files into your local `~/.m2/repository` so other projects can use this project|
|`mvn clean install -DskipTests`|This command execute the same process than the before command, except the tests|
|``||
|``||
|``||
|``||