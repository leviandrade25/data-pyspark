# Select a column or Multiple columns
The select method in PySpark is a powerful operation used to project a subset of columns from a DataFrame, allowing for efficient data manipulation and analysis. This method is fundamental in the process of transforming and managing big data sets in Spark, as it helps in refining the data structure to fit the needs of your analysis or application.
```python

from pyspark.sql import SparkSession
from pyspark.sql import Row

spark = SparkSession.builder\
.config("spark.app.name","sparksession")\
.getOrCreate()

data = [Row(name="levi",surname="Andrade",city="suzano"),
        Row(name="Bill",surname="Gates",city="New york"),
        Row(name="ClienteA",surname="SurnameClienteASurnameClienteA",city="New york"),
        Row(name="Clienteb",surname="SurnameClientebSurnameClienteA",city="New york")]

df = spark.createDataFrame(data)

columns = df.columns

df.select([c for c in df.columns]).show()

df.select("name").show()

df.select("surname","name").show()


