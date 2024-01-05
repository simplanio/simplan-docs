# Spark Properties

Simplan allows you to configure Spark properties for your Spark application. You can configure Spark properties in the following way.

!!! Limitations

    Only spark properties that can be modified after SparkContext is created can be configured using Simplan.
    
    For example, you can configure `spark.serializer` but not `spark.master` or `spark.driver.memory` using this method.


    
```js linenums="1"
simplan {
  system {
    config {
      spark {
        properties {
          "spark.serializer" = org.apache.spark.serializer.KryoSerializer
          key1 = value1
          ...
          ...
          keyN = valueN
        }
      }
    }
  }
}
```