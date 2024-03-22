# Json
PySpark offers robust capabilities for processing JSON data, a common format for storing structured data. Leveraging PySpark's distributed computing power, you can efficiently read and manipulate JSON files of varying sizes.

# Watch a video about [Read Json](https://www.youtube.com/watch?v=OvwNTDR1_WE)

```python

from pyspark.sql import SparkSession
from pyspark.sql.functions import *


spark = SparkSession.builder\
  .config("spark.app.name", "sparksession")\
  .getOrCreate()

schema = "name string, surname string, age int"

df = (spark.read.format("json")
           .schema(schema)
           .option("multiline","true")
           .load("/home/levi/simple_json.json"))

df.show()