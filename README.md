# Stata_Code

Welcome to my Stata code repository! For now, I have stored the commands that I wrote for Stata during my practical sessions while at University of York. Below, you'll find a brief overview of every .do file along with some summary statistics for the datasets that I have used in them. You can find all the datasets that I have used in this repository [here](https://github.com/DebarunG/Datasets).

### Discrete Choice Models
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

### Limited Dependent Variable Models
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
