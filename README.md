# io.dashaun.function.azure.helloworld
Building an Azure Function with Microsoft OpenJDK 16.0.1
using "local" azure functions for testing

This can't be deployed using Java 16, so I downgraded to Java 11.

## Steps To Build
I don't have Maven installed, so I used the latest version via a Docker image to build from the archetype and install the maven wrapper.
```bash
docker run -it --rm -v "$PWD":/usr/src/mymaven -v "$HOME/.m2":/root/.m2 -v "$PWD/target:/usr/src/mymaven/target" -w /usr/src/mymaven maven mvn archetype:generate -DarchetypeGroupId=com.microsoft.azure -DarchetypeArtifactId=azure-functions-archetype -DjavaVersion=16
docker run -it --rm -v "$PWD":/usr/src/mymaven -v "$HOME/.m2":/root/.m2 -v "$PWD/target:/usr/src/mymaven/target" -w /usr/src/mymaven maven mvn -N io.takari:maven:wrapper
```

## Quickstart

```bash
./mvnw azure-functions:run
```

## Deploy

You will need to create a unique function name before doing this.

```bash
./mvnw azure-functions:deploy
```

You will see something like this:
```markdown
[INFO] HTTP Trigger Urls:
[INFO]   httpexample : https://dashaun-azure-helloworld.azurewebsites.net/api/httpexample
```