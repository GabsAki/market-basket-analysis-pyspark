# Market basket analysis

## Project motivation
Someone once asked me to help them run a Market basket analysis using python for a huge dataset.

The dataset was so large that the person was having trouble running it on Google Colab using the `mlxtend` library with `pandas`.

I wondered if there was an implementation that could help in `pyspark`, but not knowing much about Market basket analysis to begin with, I wasn't able to find anything to help on time.

With this situation in mind I developed this repository as a way of studying.

I had the following main objectives:
- Learn more about Market basket analysis
- Learn if there are implementations for it in `pyspark`

## 1. Market basket analysis using `mlxtend`
This fist notebook follows the steps of [this article](https://365datascience.com/tutorials/python-tutorials/market-basket-analysis/).

The objective here was to learn more about Market basket analysis in general, and the `mlxtend` implementation that seems to be have pretty popular usage.

## 2. MBA using `pyspark` - Manual implementation
The second notebook follows [this article](https://towardsdatascience.com/big-data-market-basket-analysis-with-apriori-algorithm-on-spark-9ab094b5ac2c) that attempts to manually implement an apriori algorithm (one of the most popular algorithms for market basket analysis, also used in the first notebook) in `pyspark`.

Here, I made an attempt to run this manual implementation on the `Groceries_dataset.csv` used by the first notebook.

However, the implementation was not efficient enough, and lost even to `mlxtend`.

All things considered, it was a nice exercise to learn more about how to use `pyspark.RDD`, since I am more used to the `pyspark.DataFrame` module.

## 3. MBA using `pyspark FPGrowth`
In this final notebook, we follow [this kaggle notebook]((https://www.kaggle.com/code/megan3/market-basket-analysis-using-pyspark)) that uses pyspark's implementation of the FPGrowth algorith, another algorithm used for Market basket analysis.

A great comparison between the Apriori algorithm and FPGrowth can be found in [this article](https://medium.com/@abnersuniga7/encontre-padr%C3%B5es-nos-seus-dados-com-apriori-e-fp-growth-4a581ec1b22) (in portuguese).

Something that is interesting is that by comparing rows from the resulting tables from this notebook to the equivalent rows from the first notebook, we find the same values for confidence, lift and support.

It seems that the algorithms converge for this dataset!

## Conclusion
Although I was not able to find an Apriori implementation in `pyspark`, the `FPGrowth` implementation seems to produce very similar, if not the same results.

Since `pyspark` can leverage the power of distributed processing and FPGrowth seems to be more efficient than Apriori, I believe we can use this combination to run a Market basket analysis in a huge dataset if we have a good enough machine cluster in our disposal.

## References: 
- [How to Perform Market Basket Analysis in Python](https://365datascience.com/tutorials/python-tutorials/market-basket-analysis/)
- [Big Data Market Basket Analysis with Apriori Algorithm on Spark](https://towardsdatascience.com/big-data-market-basket-analysis-with-apriori-algorithm-on-spark-9ab094b5ac2c)
- [Market Basket Analysis using PySpark](https://www.kaggle.com/code/megan3/market-basket-analysis-using-pyspark)
- [Minerações de dados frequentes com Apriori e FP Growth](https://medium.com/@abnersuniga7/encontre-padr%C3%B5es-nos-seus-dados-com-apriori-e-fp-growth-4a581ec1b22)