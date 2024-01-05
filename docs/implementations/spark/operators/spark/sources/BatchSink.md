# Batch Sink (Generic Operator)

Writes a dataframe to a location in a specific format.

## Operator Definition

| Short Name | Fully Qualified Name |
|-----------|-------------|
| BatchSink |  com.intuit.data.simplan.spark.core.operators.sinks.batch.BatchSink |


## Configuration

``` javascript
WriteData {
  action {
    operator = BatchSink
    config = {
      source = sourceDataFrame
      format = <PARQUET | AVRO | ORC | JSON | CSV | TEXT | JDBC>
      location = /path/to/file/or/directory
      repartition = {
        enabled = true
        numberOfPartitions = 10
        columns = ["col1", "col2"]
        hint = "tableName or /path/to/file/or/directory"
        optimalFileSize = 128
        defaultNumOfPartitions = 10
      }
      partitionBy = ["col1", "col2"]
      options = {
        "option1" = "value1"
      }
    }
  }
}
```

## Parameters

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
| source | Dataframe to write to the location. | Yes | NA |
| format | Format of the file. | No | parquet |
| location | Path to the file or directory to write to. | Yes | NA |
| repartition | Logically repartition the data before writing. | No | NA |
| partitionBy | Physically Partition the data before writing. | No | NA |
| options | Options to be passed to the writer. | No | NA |

# Repartition Section

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
| enabled | Enable repartitioning. | No | false |
| numberOfPartitions | Number of partitions to repartition to. | No | NA |
| columns | Columns to repartition on. | No | NA |
| hint | Hint to repartition. <br /> Either a Catelog registered table name or a path to and S3 file can be provided. | No | NA |
| optimalFileSize | Optimal file size to repartition to in MB | No | 128 |
| defaultNumOfPartitions | Default number of partitions to repartition to. | No | {spark-default} |


## Sub Operators

The following are the sub operators of BatchSource operator. These operators are used to read specific file formats from a location. Instead of specifying the format in the configuration, the sub operator can be used to read the file. All the parameters of the sub operator are same as the parameters of the BatchSource operator.

| Short Name | Fully Qualified Name |
|-----------|-------------|
| AvroBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.AvroBatchSink |
| ParquetBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.ParquetBatchSink |
| JSONBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.JSONBatchSink |
| CSVBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.CSVBatchSink |
| JDBCBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.JDBCBatchSink |
| KafkaBatchSink | com.intuit.data.simplan.spark.core.operators.sinks.batch.KafkaBatchSink |
