# Create SparkSession
**SparkSession** in PySpark is a unified entry point for programming Spark with the Dataset and DataFrame API. Introduced in Spark 2.0, it essentially replaced SQLContext and HiveContext for working with structured data. Through SparkSession, you can access all Spark functionality: you can create DataFrames, register DataFrames as tables, execute SQL queries, cache tables, and read data from various sources. It's used to configure Spark's various settings and initiate Spark jobs. At this point we're just creating the spark app, given a name, letter on we'll discuss other points and configurations.

# Watch a video about it

["Create SparkSession"](https://www.youtube.com/watch?v=tdRpa8dGZdg&feature=youtu.be)

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder\
.config("spark.app.name","sparksession")\
.getOrCreate()

