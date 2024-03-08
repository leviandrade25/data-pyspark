# Show Dataframe
In PySpark, the show method is a fundamental operation for displaying the contents of a DataFrame in a tabular format. It's primarily used for debugging and exploratory data analysis, providing a quick glance at the data you're working with. By default, show displays the first 20 rows of the DataFrame.
## When to Use show
The show method is most useful in the following scenarios:
- Debugging: To verify the output of data transformation operations, such as filtering, aggregation, or joining datasets.
- Data Exploration: When you're initially exploring a dataset and want to get a sense of its structure, content, and the type of data each column contains.
- Quick Data Inspection: In interactive notebooks or REPL environments, where you want to quickly inspect changes to your dataset after applying certain operations.

## Best Practices
While the show method is incredibly helpful, using it effectively requires following some best practices to ensure efficiency and clarity in your PySpark applications:
- Limit Row Output for Large Datasets: Large datasets can significantly slow down your application if you attempt to display too many rows at once. Use the n parameter to limit the number of rows displayed, e.g., df.show(n=5).
- Use truncate to Manage Wide DataFrames: Wide DataFrames with many columns can result in unreadable output. Use the truncate parameter to limit the character length of each column value displayed, e.g., df.show(truncate=50).
- Avoid show in Production Code: The show method is primarily intended for interactive use and debugging. In production code, relying on actions like count, collect, or writing data to storage is more appropriate.

# Watch a video about it [Show Dataframe](https://youtu.be/Y5R3M0Ne9T0)
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

df.show(n=3)

df.show(n=10,truncate=10, vertical=False)