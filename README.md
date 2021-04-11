# Data Hack 2021 Report Prosperity Track II

Team: Tanuki
Members: Takashi Yabuta, Anurag Pamuru, Mizuki Kadowaki, Laura Diao

## Introduction
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

## Data

Due to contract terms, we were not granted access to the results from the Gallup World Poll. Because of this, 
we removed variables that we did not have access to and only kept datapoints which had values for all variables.

In order to accomplish the task of finding which countries saw the highest prosperity growth over the period from
2007 to 2014, we calculated the Prosperity Score as the arithmetic mean of the scores for all pillars for each individual Country.
We then found the average growth/change in this metric over the 8 years for which we had data. These table manipulations gave us access
to the names of the top 5 countries in terms of "Average Prosperity Growth Per Year", which are seen below.


## Observations

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

## Data visualization

![Figure of Global Prosperity Growth by Regions](./images/prosperity_map.png "Global Prosperity Growth by Regions")

- Here we have a regional analysis of changes in global prosperity over the 8 year period. 
- It is important to note that low growth can correlate to both economically stagnated countries or highly developed countries
    - For example, Australia and Afghanistan could both have similar levels of prosperity growth because nothing changed dramatically in both countries. However, both nations obviously have drastically different standards of living.
## Machine Learning Method

![Figure of Accuracy with Different PCA](./images/pca_plot.png)

## Predictions

![Figure of Forecasts](./images/forecasts.png)

## Conclusion
