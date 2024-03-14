# Group By
In PySpark, the groupBy method is a powerful tool used for aggregating data. This functionality is essential when working with large datasets, as it allows analysts and data scientists to perform computations over subsets of data defined by one or more columns. Essentially, groupBy groups the DataFrame based on the specified columns, then, various aggregation functions can be applied to these groups to generate summary statistics or insights.

# Watch a video about [GroupBy](https://www.youtube.com/watch?v=oC1e5cVoE_k)

```python

from pyspark.sql import SparkSession
from pyspark.sql import Row
from pyspark.sql.functions import col
from pyspark.sql import functions as F

spark = SparkSession.builder\
  .config("spark.app.name", "sparksession")\
  .getOrCreate()

data = [Row(Item="ItemA", price=12.04),
        Row(Item="Itemb", price=23.10),
        Row(Item="Itemc", price=43.12),
        Row(Item="Itemd", price=15.09),
        Row(Item="ItemA", price=12.04),
        Row(Item="Itemb", price=23.10),
        Row(Item="Itemc", price=43.12),
        Row(Item="Itemd", price=15.09),
        Row(Item="Iteme", price=00.00),

        ]

df = spark.createDataFrame(data)


# Sum the total sell by items
df.groupBy(col("Item")).agg(
                             F.sum(col("price")).alias("Total"),
                             (F.sum(col("price")) - 10).cast("float").alias("Total_less_10")
                             ).show(truncate=False)


data = [Row(name="levi", surname="Andrade", age="40"),
        Row(name="Bill", surname="Gates", age="20"),
        Row(name="ClienteA", surname="SurnameClienteASurnameClienteA", age="40"),
        Row(name="Clienteb", surname="SurnameClientebSurnameClienteA", age="40"),
        Row(name="ClienteA", surname="SurnameClienteASurnameClienteA", age="40"),
        Row(name="Clienteb", surname="SurnameClientebSurnameClienteA", age="40")
        ]

df = spark.createDataFrame(data)

# Getting rid of duplicates
df.groupBy([c for c in df.columns]).agg({}).show(truncate=False)
