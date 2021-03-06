# lambda-dbf-to-csv project

The default handler expects to be triggered by a SNS topic containing a S3 ObjectCreated notification.  


### Properties

|name|default|description|
|-|-|-|
|quarkus.s3.aws.region|us-east-2|The aws region to use|
|quarkus.s3.aws.credentials.type|default| default/static|
|quarkus.s3.aws.credentials.static-provider.access-key-id|null|The aws key to use when 'static' is chosen as type|
|quarkus.s3.aws.credentials.static-provider.secret-access-key|null|The aws secret to use when 'static' is chosen as type|
|destination.bucket|outbound|The URL of the outbound SQS notification queue
|destination.keyname.find|^(.*)\\.(dbf|DBF)$|The regex used to search the s3 object key name|
|destination.keyname.replace|$1.csv|The regex used to replace the s3 object key match result|






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

If you want to build an _über-jar_, execute the following command:
```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

## Creating a native executable

You can create a native executable using: 
```shell script
./mvnw package -Pnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/lambda-dbf-to-csv-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.html.

## Related guides

- AWS Lambda ([guide](https://quarkus.io/guides/amazon-lambda)): Write AWS Lambda functions

## Provided examples

### Amazon Lambda Integration example

This example contains a Quarkus Greeting Lambda ready for Amazon.

[Related guide section...](https://quarkus.io/guides/amazon-lambda)

> :warning: **INCOMPATIBLE WITH DEV MODE**: Amazon Lambda Binding is not compatible with dev mode yet!
