# Data Hack 2021 Report Prosperity Track II

Team: Tanuki
Members: Takashi Yabuta, Anurag Pamuru, Mizuki Kadowaki, Laura Diao

## INTRODUCTION
(a. Introduction to data)
Our dataset contains score values and rankings for 9 different societal pillars from 149 different countries from the years 2007-2014. Each pillar has multiple subcategories that contributed to the category ranking and score. 
The societal pillars are as follows:

- Business
- Economy
- Education
- Natural Environment
- Governance
- Health
- Personal Freedom
- Safety and Security
- Social Capital 

## DATA

Due to contract terms, we were not granted access to the results from the Gallup World Poll. Because of this, 
we removed variables that we did not have access to and only kept datapoints which had values for all variables.

In order to accomplish the task of finding which countries saw the highest prosperity growth over the period from
2007 to 2014, we calculated the Prosperity Score as the arithmetic mean of the scores for all pillars for each individual Country.
We then found the average growth/change in this metric over the 8 years for which we had data. These table manipulations gave us access
to the names of the top 5 countries in terms of "Average Prosperity Growth Per Year", which are seen below.


## OBSERVATIONS

| Country     | Average Prosperity Growth Per Year  | Most Important Pillar |
|-------------|-------------------------------------|-----------------------|
| Togo        | 0.955408                            | Safety and Security   |
| Zimbabwe    | 0.904582                            | Governance            |
| Chad        | 0.820001                            | Education             |
| Georgia     | 0.800023                            | Health                |
| Macedonia   | 0.745948                            | Social Capital        |

We calculated the most important pillar for each nation by seeing which pillar score was furthest in absolute distance
from the Prosperity Score each year. Then, we found which pillar was most frequently furthest from the prosperity across
all 8 years, which gives us the "Most Important Pillar" in determining the Prosperity Growth.

After doing so, we then trained a linear regression model on all the categories of each pillar and then peek into the 
models to find the largest linear regression coefficients of each pillar, which should ideally be correlated with 
the most important categories in that pillar. Here they are, listed with their coefficients.

| Most Impactful Categories for Business | Coefficient |
|----------------------------------------|-------------|
| ippr                                   | 2.4785      |
| logis                                  | 2.040       |
| affs                                   | 2.024       |

| Most Impactful Categories for Economy | Coefficient |
|---------------------------|-------------|
| gdp5                      | 18.610      |
| eqi                       | 5.717       |
| amp                       | 2.674       |

GDP is the greatest determiner of Economy.

| Most Impactful Categories for Education | Coefficient |
|------------------------------------|-------------|
| qslnl                              | 1.714       |
| Ginih15                            | -13.976     |
| gbrata                             | -17.244     |

| Most Impactful Categories for Environment | Coefficient |
|------------------------------------|-------------|
| pestreg                            | 0.375       |
| improved_drinkwater                | 0.224       |
| airpollution                       | -18.581     |

Air pollution is the greatest determiner of Environmental Health.

| Most Impactful Categories for Governance | Coefficient |
|------------------------------------|-------------|
| womenparl                          | 7.635       |
| rlaw                               | 2.632       |
| geff                               | 2.537       |

More women in Parliament correlates to a stronger government!

| Most Impactful Categories for Health | Coefficient |
|------------------------------------|-------------|
| leb                                | 0.253       |
| tblnl                              | -0.258      |
| meandiabetes                       | -0.444      |

Diabetes prevalence is the greatest determiner of national health

| Most Impactful Categories for Personal Freedom | Coefficient |
|------------------------------------|-------------|
| propright                          | 6.759       |
| lgbt_rights                        | 4.285       |
| deathpen                           | -7.695      |

The Death penalty/Capital Punishment is the greatest determiner of a nation's beliefs on personal freedom

| Most Impactful Categories for Safety & Security | Coefficient |
|------------------------------------|-------------|
| warcasual                          | -1.599      |
| pts                                | -3.069      |
| homilnl                            | -3.507      |

Homicide/murder is the best determiner of a nation's safety standards.

| Most Impactful Categories for Social Capital | Coefficient |
|------------------------------------|-------------|
| vtf                                | 0.141       |

## DATA VISUALIZATION

![Figure of Global Prosperity Growth by Regions](./images/prosperity_map.png "Global Prosperity Growth by Regions")

- Here, on the right, we have a regional analysis of changes in global prosperity over the 8 year period. 
    - It is important to note that low growth can correlate to both economically stagnated countries or highly developed countries
        - For example, Australia and Afghanistan could both have similar levels of prosperity growth because nothing changed dramatically in both countries. However, both nations obviously have drastically different standards of living.
- Meanwhile, on the left we have a ranking of which continent was the global leader in prosperity growth each year.
    - There is no clear winner here; however, Africa seems to be the most consistent leader in growth.

![Figure of Average Prosperity Growth for Top 5 Rising Nations](./images/prosperity_top_5.png "Average Prosperity Growth for Top 5 Rising Nations")


## MACHINE LEARNING METHODS

### Methods

[Vector Autoregression](https://towardsdatascience.com/multivariate-time-series-forecasting-653372b3db36)

### Hyperparameter tuning and PCA
![Figure of Accuracy with Different PCA](./images/pca_plot.png)

## Predictions

![Figure of Forecasts](./images/forecasts.png)

**Pillar Value Predictions for 2015**

|    | country   |    busi |   rank_busi |    econ |   rank_econ |    educ |   rank_educ |    envi |   rank_envi |    gove |   rank_gove |    heal |   rank_heal |    pers |   rank_pers |    safe |   rank_safe |    soci |   rank_soci |
|---:|:----------|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|
|  0 | Georgia   | 52.9735 |          79 | 59.9654 |          61 | 59.1949 |          85 | 53.4916 |          28 | 54.0779 |          98 | 65.9174 |          46 | 56.0263 |          71 | 66.28   |          76 | 45.3822 |          48 |
|  1 | Macedonia | 55.536  |          88 | 59.253  |          56 | 66.4805 |         120 | 64.9589 |          94 | 51.2761 |          88 | 72.848  |          84 | 55.64   |          70 | 76.0674 |         114 | 45.0173 |          44 |
|  2 | Chad      | 39.7406 |          14 | 45.7739 |          10 | 21.5546 |           2 | 55.9769 |          44 | 25.3702 |           5 | 47.9827 |           4 | 36.2053 |          16 | 56.4767 |          26 | 39.8931 |          12 |
|  3 | Togo      | 45.6765 |          31 | 50.8053 |          28 | 32.023  |          13 | 58.3408 |          56 | 34.2592 |          19 | 54.1159 |          11 | 54.1778 |          66 | 61.3347 |          49 | 39.3812 |           9 |
|  4 | Zimbabwe  | 48.1731 |          45 | 60.0522 |          63 | 47.0835 |          41 | 53.439  |          27 | 36.7532 |          30 | 68.2035 |          52 | 41.5871 |          30 | 61.4612 |          50 | 46.5467 |          58 |

**Pillar Value Predictions for 2016**

|    | country   |    busi |   rank_busi |    econ |   rank_econ |    educ |   rank_educ |    envi |   rank_envi |    gove |   rank_gove |    heal |   rank_heal |    pers |   rank_pers |    safe |   rank_safe |    soci |   rank_soci |
|---:|:----------|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|--------:|------------:|
|  0 | Georgia   | 50.5652 |          58 | 61.4895 |          64 | 57.6592 |          76 | 51.3529 |          28 | 52.6507 |          87 | 63.3463 |          42 | 57.1895 |          73 | 66.8425 |          74 | 46.5718 |          53 |
|  1 | Macedonia | 53.5217 |          77 | 59.4928 |          50 | 65.5915 |         114 | 57.7827 |          55 | 49.1805 |          75 | 70.7027 |          69 | 56.6112 |          71 | 74.8046 |         112 | 43.1385 |          24 |
|  2 | Chad      | 42.8513 |          29 | 45.6832 |           9 | 22.6597 |           3 | 57.1193 |          50 | 25.9784 |           7 | 49.6053 |           5 | 36.2493 |          20 | 61.3478 |          50 | 40.4285 |          15 |
|  3 | Togo      | 45.6366 |          36 | 50.5939 |          26 | 29.5387 |           9 | 56.0203 |          46 | 30.512  |          17 | 54.501  |          13 | 45.9548 |          40 | 67.8589 |          81 | 41.2209 |          17 |
|  4 | Zimbabwe  | 42.1331 |          26 | 66.2768 |          92 | 53.7926 |          66 | 55.3031 |          39 | 42.7921 |          55 | 73.1755 |          83 | 48.9734 |          50 | 67.7488 |          80 | 57.6737 |         116 |

**Prosperity Predictions for 2015**

|    | country   |   proseprity |   rank_proseprity |
|---:|:----------|-------------:|------------------:|
|  0 | Georgia   |      57.0344 |                68 |
|  1 | Macedonia |      60.7864 |                96 |
|  2 | Chad      |      40.9971 |                 6 |
|  3 | Togo      |      47.7905 |                22 |
|  4 | Zimbabwe  |      51.4777 |                35 |

**Prosperity Predictions for 2016**

|    | country   |   proseprity |   rank_proseprity |
|---:|:----------|-------------:|------------------:|
|  0 | Georgia   |      56.4075 |                68 |
|  1 | Macedonia |      58.9807 |                82 |
|  2 | Chad      |      42.4359 |                 8 |
|  3 | Togo      |      46.8708 |                23 |
|  4 | Zimbabwe  |      56.4299 |                69 |

## CONCLUSION

We did so great!