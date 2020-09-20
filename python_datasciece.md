# Python for Data Science 

#### Zscore

#### Percentual Change

# Statistics

Use numpy.

#### Histogram

* Bins
  Commom rule is the Square root of number of samples.

#### ECDF - Empirical cumulative distribution function

```
def ecdf(data):
    """Compute ECDF for a one-dimensional array of measurements."""
    # Number of data points: n
    n = len(data)

    # x-data for the ECDF: x
    x = np.sort(data)

    # y-data for the ECDF: y
    y = np.arange(1, n + 1) / n

    return x, y
```
ECDF
plt.plot(data, ecdf(data))

Start to see the histogram, than warplot, ECDF.

#### Percentile

Mean == 50% Percentile
np.percentile()

#### Box Plot

[75, 50, 25] percentage quatiles
IQR - Inter Quantile Range - Inside the box plot.
1,5IQR - Extreme.
2 x IQR - More is considered outlier.

#### Variance
 
Variance of the data.
 
#### Standard deviation

std = sqrt(var)
  
#### Covariance

It has dimension.
 
#### Person correlation coefficient

Measure covariance too but dimensionless.
Between -1 and 1.

#### Statistical inference


