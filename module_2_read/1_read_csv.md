# Reading CSV Files with PySpark
PySpark provides a convenient way to read CSV files using its DataFrame API. DataFrames are distributed collections of data, similar to tables in a relational database, which can be manipulated using various operations provided by PySpark.

To read a CSV file into a PySpark DataFrame, you typically use the spark.read.csv() method. This method takes the file path as input and returns a DataFrame representing the data in the CSV file.

# Watch a video about [Read csv](https://youtu.be/WHWwg2XlYTQ)

```python

from pyspark.sql import SparkSession
from pyspark.sql.functions import col
from pyspark.sql import functions as F

spark = SparkSession.builder\
       .config("spark.app.name", "sparksession")\
       .getOrCreate()

df = (spark.read
           .format("csv")
           .option("header","true")
           .option("sep","|")
           .load("/home/levi/names.csv"))

df.show()