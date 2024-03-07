# Create DataFrame
A DataFrame in PySpark is a distributed collection of data organized into named columns, similar to a table in a relational database or a DataFrame in pandas, but with richer optimizations under the hood. PySpark DataFrames are used for handling large datasets across multiple computers, allowing for big data processing and analysis. They support a wide range of operations such as selection, filtering, aggregation, and more, enabling efficient data manipulation and analysis in a distributed environment.
This is an example of a simple dataframe.
In this example we imported the Row to create rows to used as a test.
As you can see, spark contains the functions and methods that you'll need to work with it.
The function createDataFrame (pay attention to snake case used here) is the function responsible to create this dataframe,
and we pass the data variable as its argument, there's other ways to do that, but lets simplify.
And finally we have 'df.show()' that returns the dataframe itself.

```python
from pyspark.sql import SparkSession
from pyspark.sql import Row

spark = SparkSession.builder\
.config("spark.app.name","sparksession")\
.getOrCreate()

data = [Row(name="Levi",surname="Andrade"),
        Row(name="Bill",surname="Gates")]

df = spark.createDataFrame(data)

df.show()
