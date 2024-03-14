# Ordering data
Ordering data is a fundamental operation in data processing that helps in understanding the data better, making it more readable, or preparing it for specific analyses. In PySpark, sorting operations can be performed on DataFrame columns using various functions and methods. These operations are crucial in data preparation, analysis, and reporting phases of data processing tasks.

# Watch a video about it [Ordering](https://www.youtube.com/watch?v=zVTkcmt6k_M&feature=youtu.be)

```python

from pyspark.sql import SparkSession
from pyspark.sql import Row
from pyspark.sql.functions import col

spark = SparkSession.builder\
  .config("spark.app.name", "sparksession")\
  .getOrCreate()

data = [Row(name="levi", surname="Andrade", age="40"),
        Row(name="Bill", surname="Gates", age="20"),
        Row(name="ClienteA", surname="SurnameClienteASurnameClienteA", age="30"),
        Row(name="Clienteb", surname="SurnameClientebSurnameClienteA", age="40"),
        Row(name="ClienteA", surname="SurnameClienteASurnameClienteA", age="40"),
        Row(name="Clienteb", surname="SurnameClientebSurnameClienteA", age="40")
        ]

df = spark.createDataFrame(data)

# Ordering by column age in descending mode. Work as the same to sort
df.orderBy(col("age").desc()).show(truncate=False)


# Ordering by column name in ascending mode and age in descending mode. Work as the same to sort
df.orderBy(col("name").asc(), col("age").desc()).show(truncate=False)


# Ordering by column age and not informing the mode will, by default, sort in asc mode. Work as the same to orderBy
df.sort(col("age")).show(truncate=False)