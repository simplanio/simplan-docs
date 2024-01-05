# Batch Source (Generic Operator)

Reads a 

## Operator Definition

| Short Name | Fully Qualified Name |
|-----------|-------------|
| BatchSource |  com.intuit.data.simplan.spark.core.operators.sources.batch.BatchSource |


## Configuration

``` javascript
ReadDataToADataframe {
  action {
    operator = BatchSource
    config = {
      location = /path/to/file
      format = <PARQUET | AVRO | ORC | JSON | CSV | TEXT | JDBC>
      schema = schemaJson("/path/to/schema.json")
      tableType = TEMP | MANAGED | NONE
      table = "table_name"
      projection = ["col1", "col2"]
      filter = "col1 > 10"
      options = {
        "option1" = "value1"
      }
      directorySortPattern = "[\\d]+~[\\d]+"
    }
  }
}
```

## Parameters

| Parameter | Description | Required | Default |
|-----------|-------------|----------|---------|
| location | Path to the file or directory to read from. | Yes | NA |
| format | Format of the file. | No | parquet |
| schema | Schema of the records in the file. | No | NA |
| tableType | Type of table that gets created. <br/> <strong>NONE</strong> - Maintained in memory as dataframe(Not usable in SQL)<br/> <strong>MANAGED</strong> - As managed table in Hive <br/> <strong>TEMP</strong> - Temperory table in Memory(Usable in SQL) | No | NONE |
| table | Name of the table to be created, if MANAGED is selected as tableType | No | {task-name} |
| projection | List of columns to be projected. | No | NA |
| filter | Filter condition to be applied. | No | NA |
| options | Options to be passed to the reader. | No | NA |
| directorySortPattern | Regex pattern to sort the files in the directory. | No | NA |

## Sub Operators

The following are the sub operators of BatchSource operator. These operators are used to read specific file formats from a location. Instead of specifying the format in the configuration, the sub operator can be used to read the file. All the parameters of the sub operator are same as the parameters of the BatchSource operator.

| Short Name | Fully Qualified Name |
|-----------|-------------|
| AvroBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.AvroBatchSource |
| ParquetBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.ParquetBatchSource |
| ORCBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.ORCBatchSource |
| JSONBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.JSONBatchSource |
| CSVBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.CSVBatchSource |
| TextBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.TextBatchSource |
| JDBCBatchSource | com.intuit.data.simplan.spark.core.operators.sources.batch.JDBCBatchSource |
