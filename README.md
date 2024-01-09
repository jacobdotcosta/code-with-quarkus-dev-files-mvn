# code-with-quarkus-dev-files-mvn

**Note:** The Quarkus code sample uses the **8081** HTTP port.

Before you begin creating an application with this `devfile` code sample, it's helpful to understand the relationship between the `devfile` and `Dockerfile` and how they contribute to your build. You can find these files at the following URLs:

* [Quarkus `devfile.yaml`](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/devfile.yaml)
* [Quarkus `Dockerfile`](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/src/main/docker/Dockerfile.jvm.staged)

1. The `devfile.yaml` file has an [`image-build` component](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/devfile.yaml#L22-L28) that points to your `Dockerfile`.
2. The [`src/main/docker/Dockerfile.jvm.staged`](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/src/main/docker/Dockerfile.jvm.staged) file contains the instructions you need to build the code sample as a container image.
3. The `devfile.yaml` [`kubernetes-deploy` component](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/devfile.yaml#L29-L40) points to a `deploy.yaml` file that contains instructions for deploying the built container image.
4. The `devfile.yaml` [`deploy` command](https://github.com/devfile-samples/devfile-sample-code-with-quarkus/blob/main/devfile.yaml#L42-L55) completes the [outerloop](https://devfile.io/docs/2.2.0/innerloop-vs-outerloop) deployment phase by pointing to the `image-build` and `kubernetes-deploy` components to create your application.

### Additional resources
* For more information about Quarkus, see [quarkus.io](https://quarkus.io/).
* For more information about devfiles, see [Devfile.io](https://devfile.io/).
* For more information about Dockerfiles, see [Dockerfile reference](https://docs.docker.com/engine/reference/builder/).

# Quarkus

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```shell script
./mvnw compile quarkus:dev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

The application can be packaged using:
```shell script
./mvnw package
```
It produces the `quarkus-run.jar` file in the `target/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/quarkus-app/lib/` directory.

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:
```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar target/*-runner.jar`.

## Creating a native executable

You can create a native executable using: 
```shell script
./mvnw package -Dnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: 
```shell script
./mvnw package -Dnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/code-with-quarkus-dev-files-mvn-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.

## Related Guides

- RESTEasy Reactive ([guide](https://quarkus.io/guides/resteasy-reactive)): A Jakarta REST implementation utilizing build time processing and Vert.x. This extension is not compatible with the quarkus-resteasy extension, or any of the extensions that depend on it.

## Provided Code

### RESTEasy Reactive

Easily start your Reactive RESTful Web Services

[Related guide section...](https://quarkus.io/guides/getting-started-reactive#reactive-jax-rs-resources)
