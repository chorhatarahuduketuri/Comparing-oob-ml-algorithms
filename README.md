# Comparing out-of-the-box machine learning algorithms on different types of datasets
How do different algorithms and models fare with different types of data?

## Types of data
To be specific, there are different types of data, and there are different types of datasets. 

Nominal, ordinal, numerical - discrete, numerical - continuous; these are examples of different types of data. 

Skew, unbalanced, sparse, kurtosis; these are attributes of datasets or the features in those datasets. 

This project aims to find out *in general* which algorithms perform well at modelling different types of data, **and** datasets with various attributes. 

Broadly speaking, there are two types of data: **qualitative** and **quantitative**.  
**Qualitative** data describes the *qualities* of something, like it's category, colour or type (whether data is qualitative or quantitative is *qualitative* data about that data.)  
**Quantitative** is the *quantity* of something - how much of something there is, or how many. Count, price, and probability are all quantitative types of data. 

### Qualitative
Qualitative data can be further split into two subcategories: unordered (nominal) and ordered (ordinal). 

#### Nominal
Nominal means categories that aren't related to each other in any ordered way such as location, name or language. There's no implicit ordering between married, civil partnership, and single, or different manufacturers of cars. 

Note that while single categories can be predicted, all nominal data can be considered as technically binaric: it either *is* a thing, or it *is not* that thing, even if there are 15 'things'. It *is* one of them, and it *is not* 14 of them. 


#### Ordinal 
Ordinal means categories that have meanings relative to one another such as satisfaction, achievement level or rankings. Bad, OK, or good, and first, second, and third, are both examples of ordinal descriptors. 

Note that ordinal data can sometimes be very much like quantitative data, and quantitative data is often simplified into ordinal data. Income levels are an example of this (especially in anonymised data), where instead of a sample having the exact income specified (e.g. £23,450), each sample has which range of incomes it is in (e.g. between £20,000 and £29,999). Other common examples are age ranges (e.g. 0-17,18-25, 26-30, etc.), education levels (e.g. primary, secondary, undergraduate, postgraduate), and satisfaction on a tick box scale of 0-10. 

### Quantitative
Quantitiative data can be further split into 3 subcategories: discrete, continuous-interval, continuous-ratio. 

#### Discrete
Discrete data is something that can be meaningfully counted in integers, and not split further between integers. e.g. how many jelly beans (assuming no halves) in the jar? How many children do you have? How many units of product have been shipped? 

#### Continuous
Continuous data is numeric data that can take values from some range of the Real Numbers, e.g. most physical measurements (height, weight, pressure, time, density, force, etc.)

There are two useful subtypes of continuous quantitative data; interval and ratio, separated by what kind of *scale* is used. 

##### Interval
Interval data is continuous numerical data that describes the difference between things, specified on a scale that is arbitrarily defined in relation to those things. As such, it cannot describe the real ratio between those things. It describes the interval difference between two measurements, but not in relation to absolute amounts because it has an arbitrary position for zero. For example, temperature in celsius is interval data, because the difference between 1C and 5C is 4C, but 5C isn't five times hotter than 1C, though you can say that the difference between 1C and 5C is half the difference between 1C and 9C. 

##### Ratio
Ratio data is continuous numberical data that describes the difference between things, specified on a scale that is non-arbitrarily defined. Specifically, it has a unique, non-arbitrary value for zero. For example, temperature on the kelvin scale, since 0K is no temperature, and 10K is twice as hot as 5K. Almost all physical measurements can be taken on ratio scales. 

### Statistical operations on different types of data
Different types of data allow for different statistical operations. The following table (a combination of three different tables from pages that can be found in my references section, as well as a data visualisation guide from kaggle), displays very useful and practical information about analyses of different types of data, that I will include as a rough summary of useful things to keep in mind: 

|Statistical operation or analytical technique|Nominal|Ordinal|Continuous Interval|Continuous Ratio|
|---|---|---|---|---|
|Equality/Inequality|X|X|X|X|
|Greater than/Less than/Ordering|-|X|X|X|
|Addition/Subtraction|-|-|X|X|
|Relative Multiplication/Division|-|-|-|X|
|Mean|-|-|X|X|
|Median|-|X|X|X|
|Mode|X|X|X|X|
|Quantifiable difference between values|-|-|X|X|
|Bar chart|X|X|-|-|
|Line chart|-|X|X|X|
|Area chart|-|X|X|X|
|Histogram|-|-|X|X|
|Scatter plot|X|-|X|X|
|Hex plot|X|-|X|X|
|Stacked bar chart|X|X|-|-|
|Bivariate line chart|-|X|X|X|
|Count bar chart|X|X|-|-|
|Box plot|X|-|X|X|
|Violin plot|X|-|X|X|

### Further reading
The only further reading I suggest is the following short (and extremely interesting) wikipedia page: https://en.wikipedia.org/wiki/Level_of_measurement, though there are further references at the end of this README. 


## Types of dataset
There is no set list of types of datasets, but there are various descriptors of datasets and descriptors of features in datasets that are of use. 

### Descriptors of datasets

#### Density and Sparsity
A particularly important thing to know about a dataset you intend to use is whether it is dense or sparse. A dense dataset has most or all of the data points filled with meaningful data, i.e. each row has data for most or all of the features. A sparse dataset has few meaningful data points, and most are either set to 0 or the equivalent of 0 for that feature if it is non-numeric. While both are useful, dense datasets contain a lot more information than sparse datasets of the same size. 

#### Balance
Balance is a description of the ratio of instances of each predictor variable in a dataset. If there are significantly more of one class than another, then the dataset is said to be unbalanced. For example, if there are 100 pictures in a dataset from which to learn the difference between cats and dogs - and only 10 of them are dogs while the other 90 are cats - then the dataset is unbalanced. Usually any ratio between classes greater than or equal to 2:1 could definitely be considered unbalanced. This introduces problems around it's usage for learning what the difference is between the two different classes. 

There are several different approaches to solving this problem, the laziest of which is to use a more sophisticated evaluation metric (e.g. precision, recall, and of course F1 score). The more effortful involve adjusting algorithms to give more weight to what it learns from the less frequent class. These more effortful solutions are outside the scope of this work, so different evaluation metrics will be considered. 


### Descriptors of dataset features

#### Skewness
Skewness is how similar the tails of a feature are. If it has low skew, then the tails are of the same size. If it is *skewed right*, or has *positive skew*, then the tail is longer on the right hand side of the graph/positive side of the feature. If it is *skewed left*, or has *negative skew*, then the tail is longer on the left hand side of the graph/positive side of the feature. 

#### Kurtosis
Kurtosis is a measure of how much of the data lies close to the centre of the distribution, and how much lies away from the centre. Higher kurtosis (>3), called *leptokurtic*, indicates more of the data lies away from the centre of the distribution, creating a peaked shape with long tails out to the sides. Lower kurtosis (<3), called *platykurtic*, indicates more of the data is closer to the centre of the distribution, creating a rounder shape with shorter tails. 

The incredibly simplified response to particularly high/low skew or kurtosis is to mean normalise the data. The reason for this is that most ML algorithms work better on normally distributed data, and very high/low skew/kurtosis stretches data away from the normal distribution shape. Mean normalisation, in addition to it's intended purpose, works to pull some data back towards a more standard normal distribution shape. More advanced responses will not be explored in this work. 


## Datasets to be analysed

- The Wine Quality dataset again, this time for a different purpose: http://archive.ics.uci.edu/ml/datasets/Wine+Quality?ref=datanews.io. 
- Continuing my interest in wine, the Wine Data Set https://archive.ics.uci.edu/ml/datasets/wine. This is a good example of a dataset with a high feature:instance ratio (~1:14), and has only 178 instances. 
- Yet another wine dataset, Wine Reviews https://www.kaggle.com/zynicide/wine-reviews. This is a larger dataset (~25,000 instances, and 11-14 features.) 
- The Iris Data Set, https://archive.ics.uci.edu/ml/datasets/iris. 
- The Breast Cancer Wisconsin (Original) Dataset, https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Original%29. 

## Models to be used

- Logistic/Linear Regression (as appropriate)
- Random Forest
- K Nearest Neighbours 
- Multi-layer Perceptron 
- Support Vector Machine
- Decision Tree
- Naive Bayes

## Format
There will be a subfolder for each dataset, with it's own jupyter notebook(s) and README.md writeup. All models will be applied to each dataset, except where it makes no sense to do so, e.g. I will not attempt to apply a decision tree model to classify image data, and I will not use a classification algorithm to predict continuous target variables. 

### References
- https://en.wikipedia.org/wiki/Statistical_data_type
- https://en.wikipedia.org/wiki/Real_number
- https://en.wikipedia.org/wiki/Level_of_measurement
- http://www.mymarketresearchmethods.com/types-of-data-nominal-ordinal-interval-ratio/
- http://blog.minitab.com/blog/understanding-statistics/understanding-qualitative-quantitative-attribute-discrete-and-continuous-data-types
- https://towardsdatascience.com/data-types-in-statistics-347e152e8bee
- https://www.kaggle.com/learn/data-visualisation
- https://www.ibm.com/support/knowledgecenter/en/SSRL5J_1.0.1/com.ibm.swg.ba.cognos.ug_cr_rptstd.10.1.1.doc/c_id_obj_desc_tables.html
- https://en.wikipedia.org/wiki/Kurtosis