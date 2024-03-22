# Pattern
PySpark, a powerful framework for distributed data processing, offers remarkable versatility when it comes to reading data from different directories. Whether your data is scattered across multiple directories or organized in a hierarchical structure, PySpark provides efficient methods to access and process it seamlessly.

# Watch a video about [Read Pattern](https://www.youtube.com/watch?v=WhcM0NcI42c)

```python

from pyspark.sql import SparkSession
from pyspark.sql.functions import *


spark = SparkSession.builder\
  .config("spark.app.name", "sparksession")\
  .getOrCreate()

schema = "name string, surname string, age int"

df = (spark.read.format("csv")
           .option("header","true")
           .schema(schema)
           .load(["/home/levi/dir1/names*","/home/levi/dir2/names*"]))

df.show()