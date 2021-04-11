# Data Hack 2021 Report Prosperity Track II

Team: Tanuki
Members: Takashi Yabuta, Anurag Pamuru, Mizuki Kadowaki, Laura Diao

## Introduction
(a. Introduction to data)
Our dataset contains score values and rankings for 9 different societal pillars from 149 different countries from the years 2007-2014. Each pillar has multiple subcategories that contributed to the category ranking and score. 
The societal pillars and subcategories are as follows:

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
(b. Your method of data cleaning)

Due to contract terms, we were not granted access to the results from the Gallup World Poll. Because of this, 
we removed variables that we did not have access to and only kept datapoints which had values for all variables.
Additionally, we also expunged all "year" columns in each of the pillar datasets.

## Observations

| Country     | Average Prosperity Grorwth Per Year | Most Important Pillar |
|-------------|-------------------------------------|-----------------------|
| Togo        | 0.955408                            | Safety and Security   |
| Zimbabwe    | 0.904582                            | Governance            |
| Chad        | 0.820001                            | Education             |
| Georgia     | 0.800023                            | Health                |
| Macedonia   | 0.745948                            | Social Capital        |

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

| Most Impactful Categories for Governance | Coefficient |
|------------------------------------|-------------|
| womenparl                          | 7.635       |
| rlaw                               | 2.632       |
| geff                               | 2.537       |

| Most Impactful Categories for Health | Coefficient |
|------------------------------------|-------------|
| leb                                | 0.253       |
| tblnl                              | -0.258      |
| meandiabetes                       | -0.444      |

| Most Impactful Categories for Persection | Coefficient |
|------------------------------------|-------------|
| propright                          | 6.759       |
| lgbt_rights                        | 4.285       |
| deathpen                           | -7.695      |

| Most Impactful Categories for Safety & Security | Coefficient |
|------------------------------------|-------------|
| warcasual                          | -1.599      |
| pts                                | -3.069      |
| homilnl                            | -3.507      |

| Most Impactful Categories for Social Capital | Coefficient |
|------------------------------------|-------------|
| vtf                                | 0.141       |

(d. Data visualizations)

![Figure of Global Prosperity Growth by Regions](./images/prosperity_map.png "Global Prosperity Growth by Regions")

![Figure of Accuracy with Different PCA](./images/pca_plot.png)


## Machine Learning Method
(e. Detailed descriptions of machine learning methods)

## Predictions
(f. Your predictive scores and ranks for the years 2015 and year 2016)

## Conclusion
(g. Final conclusions)