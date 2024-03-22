# Text
PySpark provides a powerful framework for distributed data processing, enabling scalable and efficient data analysis on large datasets. One common task in data processing is reading text files, which can contain structured or unstructured data.

# Watch a video about [Read Text](https://www.youtube.com/watch?v=Cs2_qR6bWKg)

```python

from pyspark.sql import SparkSession
from pyspark.sql.functions import *


spark = SparkSession.builder\
  .config("spark.app.name", "sparksession")\
  .getOrCreate()

df = (spark.read
           .format("csv")
           .option("header", "false")
           .load("/home/levi/positional.txt"))

df.show()