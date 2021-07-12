# Stata_Code

Welcome to my Stata code repository! I have stored the commands that I wrote for Stata during my practical sessions while at University of York. Below, you'll find a brief overview of every .do file (converted to .txt for GitHub) along with some summary statistics for the datasets that I have used in them, in the same order that they are available in the repository. You can find all the datasets that I have used in this repository [here](https://github.com/DebarunG/Datasets).

## Discrete Choice Models
I used the [Grogger](https://github.com/DebarunG/Datasets/blob/a453afbcb3bfd54e55a98b8d6fc286300f0d8d38/GROGGER.csv) dataset to analyze the effects of prior behaviour and other characteristics (such as race, prior convictions and birth year) of a sample of people, on the probability of them being arrested in 1986. Summary statistics of the key variables used in the regressions are given below. 

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
   arr86  = 1 if arrested in 1986
   arr86    2725      0.3      0.4      0.0      0.0      0.0      1.0      1.0

    pcnv  proportion of prior convictions
    pcnv    2725      0.4      0.4      0.0      0.0      0.3      0.7      1.0

  avgsen  avg sentence length, mos.
  avgsen    2725      0.6      3.5      0.0      0.0      0.0      0.0     59.2

 tottime  time in prison since 18 (mos.)
 tottime    2725      0.8      4.6      0.0      0.0      0.0      0.0     63.4

 ptime86  mos. in prison during 1986
 ptime86    2725      0.4      2.0      0.0      0.0      0.0      0.0     12.0

   inc86  legal income, 1986, $100s
   inc86    2725     55.0     66.6      0.0      0.4     29.0     90.1    541.0

   black  =1 if black
   black    2725      0.2      0.4      0.0      0.0      0.0      0.0      1.0

  hispan  =1 if Hispanic
  hispan    2725      0.2      0.4      0.0      0.0      0.0      0.0      1.0

  born60  =1 if born in 1960
  born60    2725      0.4      0.5      0.0      0.0      0.0      1.0      1.0
-------------------------------------------------------------------------------

```
The dependent variable of interest in all the models used here is **arr86**, which equals 1 if a person was arrested in 1986. Like the name of this file suggests, I used a couple of discrete choice models to find a good fit for the data on hand. The models used are a Linear Probability Model and a Probit model. 

For the LPM, I used joint significance tests post-estimation, and for the Probit model I used the in-built Wald test as well as the likelihood-ratio test for joint significance. 

## Limited Dependent Variable Model
I used the [Fringe](https://github.com/DebarunG/Datasets/blob/a453afbcb3bfd54e55a98b8d6fc286300f0d8d38/FRINGE.csv) dataset to analyse the relationship between pension benefit amount and characteristics such as age, sex, gender for a sample of people (both working age and retired). Summary statistics of the key variables used in the regressions are given below. 

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
 peratio  pension/annearn
 peratio     616     0.05     0.04     0.00     0.00     0.05     0.07     0.21

 pension  $ value of employee pension
 pension     616   652.34   619.12     0.00     0.00   504.12  1230.22  2880.27

   exper  years work experience
   exper     616    18.62    12.33     0.00     9.00    16.00    27.00    60.00

     age  age in years
     age     616    37.65    12.70    16.00    27.00    35.00    47.00    80.00

  tenure  years with current employer
  tenure     616     7.75     7.78     0.50     2.00     4.00    15.00    25.00

    educ  years schooling
    educ     616    12.51     2.73     6.00    12.00    12.00    13.00    18.00

 depends  number of dependents
 depends     616     1.23     1.41     0.00     0.00     1.00     2.00     7.00

 married  =1 if married
 married     616     0.69     0.46     0.00     0.00     1.00     1.00     1.00

   white  =1 if white
   white     616     0.91     0.29     0.00     1.00     1.00     1.00     1.00

    male  =1 if male
    male     616     0.64     0.48     0.00     0.00     1.00     1.00     1.00
-------------------------------------------------------------------------------
```

The dependent variables of interest in this case were:
* **Pension**: value of an employee's pension in Dollars and,
*  **peratio**: the ratio of pension to annual earnings.

The only model used for regression here was the Tobit model, but the emphasis was on understanding the difference in benefits that arise from race and gender, particularly the difference between white males and non-white females.

## Linear IV Regression
I used two datasets here, namely:
* [BWGHT](https://github.com/DebarunG/Datasets/blob/main/BWGHT.csv) and,
* [WAGE2](https://github.com/DebarunG/Datasets/blob/main/WAGE2.csv).

The **BWGHT** dataset was based on survey of mothers who smoke and was used to determine the effects of several indicator variables (such as family income, the cigarette tax in the state, father's and mother's education, race of the mother, packs of cigarettes smoked in a day) on the birth weight of infants. Summary statistics of variables used from the dataset is given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
  lbwght  log of bwght
  lbwght    1388      4.8      0.2      3.1      4.7      4.8      4.9      5.6

    male  =1 if male child
    male    1388      0.5      0.5      0.0      0.0      1.0      1.0      1.0

  parity  birth order of child
  parity    1388      1.6      0.9      1.0      1.0      1.0      2.0      6.0

 lfaminc  log(faminc)
 lfaminc    1388      3.1      0.9     -0.7      2.7      3.3      3.6      4.2

   packs  packs smked per day while preg
   packs    1388      0.1      0.3      0.0      0.0      0.0      0.0      2.5

cigprice  cig. price in home state, 1988
cigprice    1388    130.6     10.2    103.8    122.8    130.8    137.0    152.5
-------------------------------------------------------------------------------
```

The dependent variable of interest in this case was **lbwght** or the log of birthweight of a baby in pounds (lbs). The main aim of this exercise was to test the validity of using the price of cigarettes as an instrumental variable for the number of packs of cigarettes smoked by the mother in a day. A Hausman test was also conducted to compare the IV and OLS regression coefficients.

The **WAGE2** dataset was used to understand the effect of birth order of a person and the number of siblings they had on their individual income. Summary statistics of the important variables in the dataset used for regressions are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
   lwage  natural log of wage
   lwage     935      6.8      0.4      4.7      6.5      6.8      7.1      8.0

    educ  years of education
    educ     935     13.5      2.2      9.0     12.0     12.0     16.0     18.0

 brthord  birth order
 brthord     852      2.3      1.6      1.0      1.0      2.0      3.0     10.0
-------------------------------------------------------------------------------
```

The regressions had relatively fewer variables, but emphasis was placed on testing the validity of birth order of a person as an IV for their level of education. 

## Linear OLS Regression
Three datasets were used for this exercise, namely:
* [discrim](https://github.com/DebarunG/Datasets/blob/main/discrim.csv),
* [SLEEP75](https://github.com/DebarunG/Datasets/blob/main/SLEEP75.csv) and,
* [hprice1](https://github.com/DebarunG/Datasets/blob/main/hprice1.csv).

The **discrim** datatset was used to see whether a sample of US restaurants charge higher prices in regions with higher concentrations of particular groups of people (such as black people, low income neighbourhoods) . Summary statistics of the variables used in the OLS regressions are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
  lpsoda  log(psoda)
  lpsoda     402      0.0      0.1     -0.3     -0.0      0.1      0.1      0.4

 prpblck  proportion black, zipcode
 prpblck     409      0.1      0.2      0.0      0.0      0.0      0.1      1.0

 lincome  log(income)
 lincome     409     10.7      0.3      9.7     10.5     10.7     10.9     11.8

  prppov  proportion in poverty, zipcode
  prppov     409      0.1      0.1      0.0      0.0      0.0      0.1      0.4

 lhseval  log(hseval)
 lhseval     409     11.8      0.4     10.4     11.6     11.9     12.1     13.1
-------------------------------------------------------------------------------
```

The dependent variable of interest was **lpsoda** or the log of the price of a medium soda from the first wave of the survey. The regressors used were:
* **prpblack**: the proportion of black people in a given zipcode,
* **lincome**: log of the median family income in a given zipcode,
* **prppov**: proportion of the population of a zipcode in poverty and,
* **lhseval**: log of the median housing value in a given zipcode.

The regressions followed simple OLS methods and a post-estimation test of joint significance was conducted for **prppov** and **lincome**.

The **SLEEP75** dataset, as its name suggests, was used to understand the effects of characteristics such as age, gender, years of schooling, and number of years had a noticeable difference in the total time spent by subjects in a survey. Summary statistics of the dataset is given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
   sleep  mins sleep at night, per wk
   sleep     706   3266.4    444.4    755.0   3015.0   3270.5   3533.0   4695.0

  totwrk  mins worked per week
  totwrk     706   2122.9    947.5      0.0   1553.0   2288.0   2693.0   6415.0

    educ  years of schooling
    educ     706     12.8      2.8      1.0     12.0     12.0     16.0     17.0

     age  in years
     age     706     38.8     11.3     23.0     29.0     36.0     48.0     65.0

   agesq  age^2
   agesq     706   1635.1    950.1    529.0    841.0   1296.0   2304.0   4225.0

  yngkid  =1 if children < 3 present
  yngkid     706      0.1      0.3      0.0      0.0      0.0      0.0      1.0

    male  =1 if male
    male     706      0.6      0.5      0.0      0.0      1.0      1.0      1.0
-------------------------------------------------------------------------------
```

The dependent variable of interest was **sleep**, which was a continuous variable that measured the number of minutes of sleep a subject had per night per week. The square of variable **age** was also used in the rgeressions to account for a nonlinear relationship between age and minutes spent sleeping. A regression of gender on the squared residuals of the main regression was perofrmed to check if there was any underlying variations which could be explained by additional variables. Heteroskedasticity-robust standard errors were used in some cases.

The main intentions behind using the **hprice1** dataset was to practice manually running the White test for heteroskedasticity. Few of the original variables were used, but more variables were generated for the purpose of this test. Summary stats of the original variables used are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
  lprice  log(price)
  lprice      88      5.6      0.3      4.7      5.4      5.6      5.8      6.6

llotsize  log(lotsize)
llotsize      88      8.9      0.5      6.9      8.6      8.8      9.1     11.4

  lsqrft  log(sqrft)
  lsqrft      88      7.6      0.3      7.1      7.4      7.5      7.7      8.3

   bdrms  number of bdrms
   bdrms      88      3.6      0.8      2.0      3.0      3.0      4.0      7.0
-------------------------------------------------------------------------------
```

## Panel Data Regressions
Here, I used two datasets, namely:
* [JTRAIN1](https://github.com/DebarunG/Datasets/blob/main/JTRAIN1.csv) and,
* [airfare](https://github.com/DebarunG/Datasets/blob/main/airfare.csv).

The **JTRAIN1** dataset was used to analyze the effects of job training grants ( as well as other factors such as the year of grant, presence of unions, and the effects of past grants) on firm scrap rates. Summary statistics for the variables used from the dataset are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
  lscrap  log(scrap)
  lscrap     162      0.4      1.5     -4.6     -0.5      0.3      1.4      3.4

     d88  = 1 if year = 1988
     d88     471      0.3      0.5      0.0      0.0      0.0      1.0      1.0

     d89  = 1 if year = 1989
     d89     471      0.3      0.5      0.0      0.0      0.0      1.0      1.0

   union  =1 if unionized
   union     471      0.2      0.4      0.0      0.0      0.0      0.0      1.0

   grant  = 1 if received grant
   grant     471      0.1      0.3      0.0      0.0      0.0      0.0      1.0
-------------------------------------------------------------------------------
```

The dependent variable of interest for all regressions was **lscrap**, which was the log of the firm's scrap rate per 100 items produced. A firm with a higher scrap rate produced more faulty products in the production line than a firm with a lower scrap rate. A preliminary OLS regression was conducted with robust clustered standard errors, clustered around the firm's code, to account for variations in a firm's performance across time. Several panel data regression models are used, namely:
* first differencing,
* fixed-effects (FE) regression,
* dummy variable (DV) regression and,
* random effects (RE) regressio,

A Breusch-Pagan test was implemented to compare the estimates obtained from pooled OLS and FE/RE regressions, then a Hausman test was was implemented to compare the estimates obtained from FE and RE regressions.

The **airfare** dataset was used to see the effects of fare and distance on passenger count in an airline. Summary statistics for variables used from **airfare** are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
   lfare  log(fare)
   lfare    4596     5.10     0.44     3.61     4.81     5.12     5.42     6.26

 lpassen  log(passen)
 lpassen    4596     6.02     0.88     0.69     5.37     5.88     6.58     9.05

  concen  = bmktshr
  concen    4596     0.61     0.20     0.16     0.47     0.60     0.75     1.00

   ldist  log(distance)
   ldist    4596     6.70     0.66     4.55     6.22     6.76     7.17     7.91

 ldistsq  ldist^2
 ldistsq    4596    45.28     8.73    20.74    38.75    45.67    51.45    62.57

     y98  =1 if year == 1998
     y98    4596     0.25     0.43     0.00     0.00     0.00     0.50     1.00

     y99  =1 if year == 1999
     y99    4596     0.25     0.43     0.00     0.00     0.00     0.50     1.00

     y00  =1 if year == 2000
     y00    4596     0.25     0.43     0.00     0.00     0.00     0.50     1.00
-------------------------------------------------------------------------------
```

Dependent variables of interest here were:
* **lfare**: log of average one-way fare for a particular route and,
* **lpassen**: log of average daily passengers for a route.

The exercises in this case were similar to the previous one with standard errors clustered around the flight routes, but with the addition of interaction terms in some of the panel data regressions.

## Quantile Regressions
The dataset used for quantile regressions was [unemp](https://github.com/DebarunG/Datasets/blob/main/unemp.csv), to analyze the effects of gender, age and other characteristics on the amount of time a person spent being unemployed. Summary statistics of the variables used for the regressions from this dataset are given below.

```
                                        -------------- Quantiles --------------
Variable       n     Mean     S.D.      Min      .25      Mdn      .75      Max
-------------------------------------------------------------------------------
   ltime  log(time)
   ltime   21685     5.39     1.32     0.00     4.39     5.50     6.48     7.69

  female  Sex (1=female)
  female   21685     0.37     0.48     0.00     0.00     0.00     1.00     1.00

     age  Age in years
     age   21685    35.50     6.74    26.00    30.00    34.00    41.00    49.00

    wage  Last daily wage while employed (in euros)
    wage   21685    61.25    34.56     0.00    43.40    61.70    79.10   204.10
-------------------------------------------------------------------------------
```

The dependent variable of interest was **ltime**, which was a continuous variable taken as the log of the number of days spent unemployed by a person. Several interaction terms were generated using the above original variables to plot estimated conditional quantiles of unemployment periods for men and women at different ages. 

The primary intention of this exercise was to illustrate the coefficients which varied for men and women at different quantiles. For example, at the 10th percentile, the functions were parallel for males and females with females having a larger intercept but for high a quantile like the 80th percentile, it was seen that young females have longer unemployment periods than young males but older females have shorter unemployment periods.
