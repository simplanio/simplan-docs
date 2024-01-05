# Deployment Options

## Simplan Launcher

Simplan launcher is a ready to go Simplan deployment which can accept authoring logic (as config files) as command line
arguments and execute it without any need for build or deployment.

**Maintained by:** Simplan Team <br/>
**Pros:** No Build/Deployment process required. <br/>
**Cons:** Supports only built in Operations. <br/>

## Simplan Launcher + Custom Operators

Works similar to the option above(Simplan Launcher), custom operators need to be built as an independent jar and
provided in classpath using `--jars` during spark-submit.

**Maintained by:** Launcher (Simplan Team) and Custom Operators (customer team) <br/>
**Pros:** Custom operators can be used. <br/>
**Cons:** CI/CD of custom operator needs to be maintained by the customer.

## Custom Launcher

Users will be able to write a custom launcher which can be used to execute Simplan jobs. This will be a standalone jar
which can be executed using spark-submit. This jar will be responsible for building the Simplan job and submitting it to
spark.

The following maven dependency needs to be added to the custom launcher project.

```xml
<dependency>
    <groupId>com.simplan</groupId>
    <artifactId>simplan-core</artifactId>
    <version>0.1.0</version>
</dependency>
```

**Maintained by:** Customer Team <br/>
**Pros:** Custom operators can be used. <br/>
**Cons:** CI/CD of custom launcher needs to be maintained by the customer.