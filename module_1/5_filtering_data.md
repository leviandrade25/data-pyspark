# Filtering data
In PySpark, the filter function is a powerful tool used to narrow down datasets based on specific criteria. It allows users to apply a condition to each row of a DataFrame or an RDD (Resilient Distributed Dataset), returning only those rows that meet the specified condition. This function is particularly useful in data processing and analysis tasks where there is a need to exclude irrelevant or unnecessary data, such as filtering out records that do not meet certain quality standards, or focusing analysis on a subset of data that meets particular criteria. By using the filter function, data engineers and scientists can efficiently manage large volumes of data, enhancing the performance of their data pipelines and making their analyses more precise and relevant. In essence, filter acts as a sieve, enabling users to focus on the most pertinent information within their datasets.

# Watch a video about it [Filtering](https://www.youtube.com/watch?v=lXE_GdphwpY)
```python

from pyspark.sql import SparkSession
from pyspark.sql import Row
from pyspark.sql.functions import col

spark = SparkSession.builder\
.config("spark.app.name","sparksession")\
.getOrCreate()

data = [Row(name="levi",surname="Andrade",age=40),
        Row(name="Bill",surname="Gates",age=20),
        Row(name="ClienteA",surname="SurnameClienteASurnameClienteA",age=40),
        Row(name="Clienteb",surname="SurnameClientebSurnameClienteA",age=40),
        Row(name="ClienteA",surname="SurnameClienteASurnameClienteA",age=40),
        Row(name="Clienteb",surname="SurnameClientebSurnameClienteA",age=40)
        ]

df = spark.createDataFrame(data)

data2 = [Row(name="levi",surname="Andrade",age=10),
        Row(name="Bill",surname="Gates",age=20),
        Row(name="ClienteA",surname="SurnameClienteASurnameClienteA",age=30),
        Row(name="Clienteb",surname="SurnameClientebSurnameClienteA",age=40)
        ]

df_simple = spark.createDataFrame(data2)

# Filtering age greater than 10
df_simple_filter = df_simple.filter(col("age") > 10)

df_simple_filter.show(truncate=False)


# Filtering age greater than 10 AND name that starts with C
multi_filter_and_like = df_simple.filter(
                                  (col('age') > 10)
                                 &(col("name").like("C%"))
                                        )

multi_filter_and_like.show(truncate=False)


# Filtering age greater than 10 AND name that do not starts with C
# The tilde symbol before col makes all the sentence inside the parentheses its inverse
multi_filter_and_not_like = df_simple.filter(
                                        (col('age') > 10)
                                        &(~col("name").like("C%"))
                                                )

multi_filter_and_not_like.show(truncate=False)

# Filtering with where age greater than 10
use_where_simple = df_simple.where("age > 10")


use_where_simple.show(truncate=False)


# Filtering with where age greater than 10 and name that ends with b
use_where_multi = df_simple.where("age > 10 and name like '%b' ")


# Filtering with where age greater than 10 and name that ends with b
use_where_multi2 = df_simple.where("age > 10").where("name like '%b'")


use_where_multi.show(truncate=False)


use_where_multi2.show(truncate=False)