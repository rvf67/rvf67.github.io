---
layout: single
title:  "logistic-regression study"
categories: coding
tag: [python, blog, jekyll]
toc: true
author_profile: false
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>


<a class="anchor" id="0"></a>

# **Logistic Regression Classifier Tutorial with Python**





**As always, I hope you find this kernel useful and your <font color="red"><b>UPVOTES</b></font> would be highly appreciated**.



<a class="anchor" id="0.1"></a>

# **Table of Contents**





1.	[Introduction to Logistic Regression](#1)

2.	[Logistic Regression intuition](#2)

3.	[Assumptions of Logistic Regression](#3)

4.	[Types of Logistic Regression](#4)

5.	[Import libraries](#5)

6.	[Import dataset](#6)

7.	[Exploratory data analysis](#7)

8.	[Declare feature vector and target variable](#8)

9.	[Split data into separate training and test set](#9)

10.	[Feature engineering](#10)

11.	[Feature scaling](#11)

12.	[Model training](#12)

13.	[Predict results](#13)

14.	[Check accuracy score](#14)

15.	[Confusion matrix](#15)

16.	[Classification metrices](#16)

17.	[Adjusting the threshold level](#17)

18.	[ROC - AUC](#18)

19.	[k-Fold Cross Validation](#19)

20.	[Hyperparameter optimization using GridSearch CV](#20)

21.	[Results and conclusion](#21)

22. [References](#22)



# **1. Introduction to Logistic Regression** <a class="anchor" id="1"></a>





[Table of Contents](#0.1)





데이터 과학자들이 새로운 분류 문제를 마주할 때, 먼저 떠오르는 알고리즘 중 하나는 로지스틱 회귀일 수 있다. 로지스틱 회귀는 관측치를 이산적인 클래스 집합에 예측하는 데 사용되는 지도 학습 분류 알고리즘이다. 실제로 관측치를 서로 다른 범주로 분류하는 데 사용된다. 따라서 출력은 이산적인 형태이다. 로지스틱 회귀는 로짓 회귀(Logit Regression)로도 불린다. 이는 분류 문제를 해결하는 데 사용되는 가장 간단하고 직관적이며 유연한 분류 알고리즘 중 하나이다.


# **2. Logistic Regression intuition** <a class="anchor" id="2"></a>





[Table of Contents](#0.1)





통계학에서 로지스틱 회귀 모델은 주로 분류 목적으로 사용되는 통계 모델로 널리 사용된다.. 즉, 주어진 일련의 관측치를 기반으로 로지스틱 회귀 알고리즘은 이러한 관측치를 두 개 이상의 이산 클래스로 분류하는 데 도움을 준다. 따라서 대상 변수는 이산적이다.



로지스틱 회귀 알고리즘은 다음과 같이 작동한다. -


## **Implement linear equation**





로지스틱 회귀 알고리즘은 독립 변수 또는 설명 변수를 사용하여 종속 변수를 예측하는 선형 방정식을 구현하여 작동합니다. 예를 들어, 우리는 공부한 시간의 양과 시험 합격 확률의 예를 고려할 수 있습니다. 여기서, 공부한 시간은 설명 변수이며 x1로 나타내며, 시험 합격 확률은 반응 또는 대상 변수이며 z로 표시됩니다.



설명 변수가 하나(x1)이고 반응 변수가 하나(z)인 경우, 선형 방정식은 다음과 같은 수식으로 표시됩니다.



z = β0 + β1x1

여기서 β0와 β1은 모델의 매개 변수입니다.



설명 변수가 여러 개인 경우, 위의 방정식은 다음과 같이 확장될 수 있습니다.



z = β0 + β1x1+ β2x2+……..+ βnxn

여기서 β0, β1, β2 및 βn은 모델의 매개 변수입니다.



따라서 예측된 반응 값은 위의 방정식으로 주어지며 z로 표시됩니다.


## **Sigmoid Function**



이러한 예측된 응답값 z는 0과 1 사이의 확률 값으로 변환됩니다. 예측된 값에서 확률 값으로 변환하기 위해 시그모이드 함수를 사용합니다. 이 시그모이드 함수는 임의의 실수 값을 0과 1 사이의 확률 값으로 매핑합니다.



기계학습에서는 시그모이드 함수를 사용하여 예측 값을 확률 값으로 매핑합니다. 시그모이드 함수는 S자 모양의 곡선을 가지고 있으며, sigmoid curve라고도 불립니다.



시그모이드 함수는 로지스틱 함수의 특수한 경우입니다. 다음과 같은 수식으로 표현됩니다.



그래프로는 다음과 같이 시그모이드 함수를 나타낼 수 있습니다.


### Sigmoid Function



![Sigmoid Function](https://miro.medium.com/max/970/1*Xu7B5y9gp0iL5ooBj7LtWw.png)


## **Decision boundary**



sigmoid 함수는 0과 1 사이의 확률 값을 반환합니다. 이 확률 값은 "0" 또는 "1"인 이산 클래스로 매핑됩니다. 이 확률 값을 이산 클래스로 매핑하기 위해서는 임계값을 선택해야 합니다. 이 임계값은 결정 경계(decision boundary)라고 합니다. 이 결정 경계 값 이상의 값은 클래스 1로 매핑하고, 이하의 값은 클래스 0으로 매핑합니다.



수학적으로는 다음과 같이 표현될 수 있습니다.



p ≥ 0.5 => 클래스 = 1



p < 0.5 => 클래스 = 0



일반적으로 결정 경계는 0.5로 설정됩니다. 따라서 확률 값이 0.8(> 0.5)인 경우 이 관측치는 클래스 1로 매핑됩니다. 마찬가지로, 확률 값이 0.2(< 0.5)인 경우 이 관측치는 클래스 0으로 매핑됩니다. 이것은 아래 그래프에서 나타납니다.


![Decision boundary in sigmoid function](https://ml-cheatsheet.readthedocs.io/en/latest/_images/logistic_regression_sigmoid_w_threshold.png)


## **Making predictions**



이제 로지스틱 회귀에서 시그모이드 함수와 결정 경계에 대해 알았습니다. 우리는 시그모이드 함수와 결정 경계에 대한 지식을 활용하여 예측 함수를 작성할 수 있습니다. 로지스틱 회귀의 예측 함수는 관측값이 양성인(Yes 또는 True) 클래스 1에 속할 확률을 반환합니다. 이는 P(class = 1)로 표시되며, 이 확률이 1에 가까워질수록 모델이 관측값이 클래스 1에 속한다고 더 자신 있게 판단할 수 있으며, 그렇지 않으면 클래스 0에 속한다고 판단할 수 있습니다.



# **3. Assumptions of Logistic Regression** <a class="anchor" id="3"></a>





[Table of Contents](#0.1)





로지스틱 회귀 모델은 몇 가지 주요 가정이 필요합니다. 이는 다음과 같습니다:



1. 로지스틱 회귀 모델은 종속 변수가 이항, 다항 또는 순서형인 것을 요구합니다.



2. 반복 측정에서 나온 것이 아닌 독립적인 관측치가 필요합니다.



3. 로지스틱 회귀 알고리즘은 독립 변수 간 다중공선성이 적거나 없어야 합니다. 즉, 독립 변수들은 서로 너무 높게 상관되어 있어서는 안 됩니다.



4. 로지스틱 회귀 모델은 독립 변수와 로그 오즈의 선형성을 가정합니다.



5. 로지스틱 회귀 모델의 성공은 샘플 크기에 따라 달라집니다. 일반적으로 높은 정확도를 달성하려면 큰 샘플 크기가 필요합니다.


# **4. Types of Logistic Regression** <a class="anchor" id="4"></a>





[Table of Contents](#0.1)





로지스틱 회귀 모델은 대상 변수 카테고리에 따라 세 가지 그룹으로 분류될 수 있습니다. 이 세 가지 그룹은 아래와 같이 설명됩니다.



### 1. 이항 로지스틱 회귀(Binary Logistic Regression)

이항 로지스틱 회귀에서 대상 변수는 두 가지 가능한 범주를 가지고 있습니다. 대표적인 예시로는 yes or no, good or bad, true or false, spam or no spam, pass or fail 등이 있습니다.



### 2. 다항 로지스틱 회귀(Multinomial Logistic Regression)

다항 로지스틱 회귀에서 대상 변수는 정해진 순서가 없는 세 개 이상의 범주를 가지고 있습니다. 즉, 세 개 이상의 명목 범주가 있습니다. 예시로는 과일의 종류 - 사과, 망고, 오렌지, 바나나 등이 있습니다.



### 3. 순서형 로지스틱 회귀(Ordinal Logistic Regression)

순서형 로지스틱 회귀에서 대상 변수는 세 개 이상의 순서형 범주를 가지고 있습니다. 즉, 범주 사이에 내재적인 순서가 있습니다. 예를 들어, 학생 성적은 poor, average, good, excellent와 같이 분류할 수 있습니다.


# **5. Import libraries** <a class="anchor" id="5"></a>





[Table of Contents](#0.1)



```python
# This Python 3 environment comes with many helpful analytics libraries installed
# It is defined by the kaggle/python docker image: https://github.com/kaggle/docker-python
# For example, here's several helpful packages to load in 

import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)
import matplotlib.pyplot as plt # data visualization
import seaborn as sns # statistical data visualization
%matplotlib inline

# Input data files are available in the "../input/" directory.
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

# Any results you write to the current directory are saved as output.
```

<pre>
/kaggle/input/weather-dataset-rattle-package/weatherAUS.csv
</pre>

```python
import warnings

warnings.filterwarnings('ignore')
```

# **6. Import dataset** <a class="anchor" id="6"></a>





[Table of Contents](#0.1)



```python
data = '/kaggle/input/weather-dataset-rattle-package/weatherAUS.csv'

df = pd.read_csv(data)
```

# **7. Exploratory data analysis** <a class="anchor" id="7"></a>





[Table of Contents](#0.1)





이제 데이터를 탐색하여 데이터에 대한 인사이트를 얻겠습니다



```python
# view dimensions of dataset

df.shape
```

<pre>
(145460, 23)
</pre>
데이터 세트에는 142193개의 인스턴스와 24개의 변수가 있음을 알 수 있습니다..



```python
# preview the dataset

df.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Location</th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustDir</th>
      <th>WindGustSpeed</th>
      <th>WindDir9am</th>
      <th>...</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>Pressure9am</th>
      <th>Pressure3pm</th>
      <th>Cloud9am</th>
      <th>Cloud3pm</th>
      <th>Temp9am</th>
      <th>Temp3pm</th>
      <th>RainToday</th>
      <th>RainTomorrow</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2008-12-01</td>
      <td>Albury</td>
      <td>13.4</td>
      <td>22.9</td>
      <td>0.6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>W</td>
      <td>44.0</td>
      <td>W</td>
      <td>...</td>
      <td>71.0</td>
      <td>22.0</td>
      <td>1007.7</td>
      <td>1007.1</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>16.9</td>
      <td>21.8</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2008-12-02</td>
      <td>Albury</td>
      <td>7.4</td>
      <td>25.1</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WNW</td>
      <td>44.0</td>
      <td>NNW</td>
      <td>...</td>
      <td>44.0</td>
      <td>25.0</td>
      <td>1010.6</td>
      <td>1007.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>17.2</td>
      <td>24.3</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2008-12-03</td>
      <td>Albury</td>
      <td>12.9</td>
      <td>25.7</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WSW</td>
      <td>46.0</td>
      <td>W</td>
      <td>...</td>
      <td>38.0</td>
      <td>30.0</td>
      <td>1007.6</td>
      <td>1008.7</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>21.0</td>
      <td>23.2</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-12-04</td>
      <td>Albury</td>
      <td>9.2</td>
      <td>28.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NE</td>
      <td>24.0</td>
      <td>SE</td>
      <td>...</td>
      <td>45.0</td>
      <td>16.0</td>
      <td>1017.6</td>
      <td>1012.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18.1</td>
      <td>26.5</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2008-12-05</td>
      <td>Albury</td>
      <td>17.5</td>
      <td>32.3</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>W</td>
      <td>41.0</td>
      <td>ENE</td>
      <td>...</td>
      <td>82.0</td>
      <td>33.0</td>
      <td>1010.8</td>
      <td>1006.0</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>17.8</td>
      <td>29.7</td>
      <td>No</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 23 columns</p>
</div>



```python
col_names = df.columns

col_names
```

<pre>
Index(['Date', 'Location', 'MinTemp', 'MaxTemp', 'Rainfall', 'Evaporation',
       'Sunshine', 'WindGustDir', 'WindGustSpeed', 'WindDir9am', 'WindDir3pm',
       'WindSpeed9am', 'WindSpeed3pm', 'Humidity9am', 'Humidity3pm',
       'Pressure9am', 'Pressure3pm', 'Cloud9am', 'Cloud3pm', 'Temp9am',
       'Temp3pm', 'RainToday', 'RainTomorrow'],
      dtype='object')
</pre>
### Drop  RISK_MM variable



It is given in the dataset description, that we should drop the `RISK_MM` feature variable from the dataset description. So, we 

should drop it as follows-



```python
#df.drop(['RISK_MM'], axis=1, inplace=True)
```


```python
# view summary of dataset

df.info()
```

<pre>
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 145460 entries, 0 to 145459
Data columns (total 23 columns):
Date             145460 non-null object
Location         145460 non-null object
MinTemp          143975 non-null float64
MaxTemp          144199 non-null float64
Rainfall         142199 non-null float64
Evaporation      82670 non-null float64
Sunshine         75625 non-null float64
WindGustDir      135134 non-null object
WindGustSpeed    135197 non-null float64
WindDir9am       134894 non-null object
WindDir3pm       141232 non-null object
WindSpeed9am     143693 non-null float64
WindSpeed3pm     142398 non-null float64
Humidity9am      142806 non-null float64
Humidity3pm      140953 non-null float64
Pressure9am      130395 non-null float64
Pressure3pm      130432 non-null float64
Cloud9am         89572 non-null float64
Cloud3pm         86102 non-null float64
Temp9am          143693 non-null float64
Temp3pm          141851 non-null float64
RainToday        142199 non-null object
RainTomorrow     142193 non-null object
dtypes: float64(16), object(7)
memory usage: 25.5+ MB
</pre>
### Types of variables





이 섹션에서는 데이터셋을 범주형 변수와 수치형 변수로 분리합니다. 데이터셋에는 범주형 변수와 수치형 변수가 혼합되어 있습니다. 범주형 변수는 데이터 타입이 object입니다. 수치형 변수는 데이터 타입이 float64입니다.



먼저 범주형 변수를 찾아보겠습니다.



```python
# find categorical variables

categorical = [var for var in df.columns if df[var].dtype=='O']

print('There are {} categorical variables\n'.format(len(categorical)))

print('The categorical variables are :', categorical)
```

<pre>
There are 7 categorical variables

The categorical variables are : ['Date', 'Location', 'WindGustDir', 'WindDir9am', 'WindDir3pm', 'RainToday', 'RainTomorrow']
</pre>

```python
# view the categorical variables

df[categorical].head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Location</th>
      <th>WindGustDir</th>
      <th>WindDir9am</th>
      <th>WindDir3pm</th>
      <th>RainToday</th>
      <th>RainTomorrow</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2008-12-01</td>
      <td>Albury</td>
      <td>W</td>
      <td>W</td>
      <td>WNW</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2008-12-02</td>
      <td>Albury</td>
      <td>WNW</td>
      <td>NNW</td>
      <td>WSW</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2008-12-03</td>
      <td>Albury</td>
      <td>WSW</td>
      <td>W</td>
      <td>WSW</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-12-04</td>
      <td>Albury</td>
      <td>NE</td>
      <td>SE</td>
      <td>E</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2008-12-05</td>
      <td>Albury</td>
      <td>W</td>
      <td>ENE</td>
      <td>NW</td>
      <td>No</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>


### Summary of categorical variables



- 데이터에는 Date 열이 있는 날짜 변수가 있습니다.

- Location, WindGustDir, WindDir9am, WindDir3pm, RainToday, RainTomorrow와 같이 총 6개의 범주-형 변수가 있습니다.

- RainToday와 RainTomorrow는 이진 범주형 변수입니다.

- RainTomorrow은 타겟 변수입니다.


## Explore problems within categorical variables





이제 범주형의 결측치를 찾아봅니다.





### Missing values in categorical variables



```python
# check missing values in categorical variables

df[categorical].isnull().sum()
```

<pre>
Date                0
Location            0
WindGustDir     10326
WindDir9am      10566
WindDir3pm       4228
RainToday        3261
RainTomorrow     3267
dtype: int64
</pre>

```python
# print categorical variables containing missing values

cat1 = [var for var in categorical if df[var].isnull().sum()!=0]

print(df[cat1].isnull().sum())
```

<pre>
WindGustDir     10326
WindDir9am      10566
WindDir3pm       4228
RainToday        3261
RainTomorrow     3267
dtype: int64
</pre>
우리는 총 4개의 결측치가 있는 범주형 데이터를 찾을 수 있습니다. `WindGustDir`, `WindDir9am`, `WindDir3pm`, `RainToday`.


### Frequency counts of categorical variables





이제 빈도 수를 확인하여 각 범주형 변수가 가지고 있는 값들의 분포를 파악할 수 있습니다.



```python
# view frequency of categorical variables

for var in categorical: 
    
    print(df[var].value_counts())
```

<pre>
2015-11-02    49
2013-06-18    49
2016-01-12    49
2016-12-08    49
2016-04-06    49
              ..
2008-01-25     1
2007-11-30     1
2007-11-05     1
2007-11-10     1
2008-01-08     1
Name: Date, Length: 3436, dtype: int64
Canberra            3436
Sydney              3344
Brisbane            3193
Perth               3193
Adelaide            3193
Hobart              3193
Melbourne           3193
Darwin              3193
Ballarat            3040
Cairns              3040
Townsville          3040
MountGinini         3040
MountGambier        3040
Albury              3040
Bendigo             3040
AliceSprings        3040
GoldCoast           3040
Launceston          3040
Albany              3040
Wollongong          3040
Newcastle           3039
Penrith             3039
Tuggeranong         3039
Witchcliffe         3009
NorfolkIsland       3009
CoffsHarbour        3009
MelbourneAirport    3009
PerthAirport        3009
Moree               3009
SydneyAirport       3009
Williamtown         3009
Portland            3009
PearceRAAF          3009
Watsonia            3009
Nuriootpa           3009
WaggaWagga          3009
Mildura             3009
Richmond            3009
Cobar               3009
Sale                3009
Dartmoor            3009
Woomera             3009
BadgerysCreek       3009
Walpole             3006
NorahHead           3004
SalmonGums          3001
Uluru               1578
Nhil                1578
Katherine           1578
Name: Location, dtype: int64
W      9915
SE     9418
N      9313
SSE    9216
E      9181
S      9168
WSW    9069
SW     8967
SSW    8736
WNW    8252
NW     8122
ENE    8104
ESE    7372
NE     7133
NNW    6620
NNE    6548
Name: WindGustDir, dtype: int64
N      11758
SE      9287
E       9176
SSE     9112
NW      8749
S       8659
W       8459
SW      8423
NNE     8129
NNW     7980
ENE     7836
NE      7671
ESE     7630
SSW     7587
WNW     7414
WSW     7024
Name: WindDir9am, dtype: int64
SE     10838
W      10110
S       9926
WSW     9518
SSE     9399
SW      9354
N       8890
WNW     8874
NW      8610
ESE     8505
E       8472
NE      8263
SSW     8156
NNW     7870
ENE     7857
NNE     6590
Name: WindDir3pm, dtype: int64
No     110319
Yes     31880
Name: RainToday, dtype: int64
No     110316
Yes     31877
Name: RainTomorrow, dtype: int64
</pre>

```python
# view frequency distribution of categorical variables

for var in categorical: 
    
    print(df[var].value_counts()/np.float(len(df)))
```

<pre>
2015-11-02    0.000337
2013-06-18    0.000337
2016-01-12    0.000337
2016-12-08    0.000337
2016-04-06    0.000337
                ...   
2008-01-25    0.000007
2007-11-30    0.000007
2007-11-05    0.000007
2007-11-10    0.000007
2008-01-08    0.000007
Name: Date, Length: 3436, dtype: float64
Canberra            0.023622
Sydney              0.022989
Brisbane            0.021951
Perth               0.021951
Adelaide            0.021951
Hobart              0.021951
Melbourne           0.021951
Darwin              0.021951
Ballarat            0.020899
Cairns              0.020899
Townsville          0.020899
MountGinini         0.020899
MountGambier        0.020899
Albury              0.020899
Bendigo             0.020899
AliceSprings        0.020899
GoldCoast           0.020899
Launceston          0.020899
Albany              0.020899
Wollongong          0.020899
Newcastle           0.020892
Penrith             0.020892
Tuggeranong         0.020892
Witchcliffe         0.020686
NorfolkIsland       0.020686
CoffsHarbour        0.020686
MelbourneAirport    0.020686
PerthAirport        0.020686
Moree               0.020686
SydneyAirport       0.020686
Williamtown         0.020686
Portland            0.020686
PearceRAAF          0.020686
Watsonia            0.020686
Nuriootpa           0.020686
WaggaWagga          0.020686
Mildura             0.020686
Richmond            0.020686
Cobar               0.020686
Sale                0.020686
Dartmoor            0.020686
Woomera             0.020686
BadgerysCreek       0.020686
Walpole             0.020665
NorahHead           0.020652
SalmonGums          0.020631
Uluru               0.010848
Nhil                0.010848
Katherine           0.010848
Name: Location, dtype: float64
W      0.068163
SE     0.064746
N      0.064024
SSE    0.063358
E      0.063117
S      0.063028
WSW    0.062347
SW     0.061646
SSW    0.060058
WNW    0.056730
NW     0.055837
ENE    0.055713
ESE    0.050681
NE     0.049038
NNW    0.045511
NNE    0.045016
Name: WindGustDir, dtype: float64
N      0.080833
SE     0.063846
E      0.063083
SSE    0.062643
NW     0.060147
S      0.059528
W      0.058153
SW     0.057906
NNE    0.055885
NNW    0.054860
ENE    0.053870
NE     0.052736
ESE    0.052454
SSW    0.052159
WNW    0.050969
WSW    0.048288
Name: WindDir9am, dtype: float64
SE     0.074508
W      0.069504
S      0.068239
WSW    0.065434
SSE    0.064616
SW     0.064306
N      0.061116
WNW    0.061006
NW     0.059192
ESE    0.058470
E      0.058243
NE     0.056806
SSW    0.056070
NNW    0.054104
ENE    0.054015
NNE    0.045305
Name: WindDir3pm, dtype: float64
No     0.758415
Yes    0.219167
Name: RainToday, dtype: float64
No     0.758394
Yes    0.219146
Name: RainTomorrow, dtype: float64
</pre>
### Number of labels: cardinality



카테고리 변수 내 라벨의 수를 카디널리티(cardinality)라고 합니다. 변수 내 라벨의 수가 많을수록(high cardinality) 머신 러닝 모델에서 심각한 문제가 발생할 수 있습니다. 따라서, 높은 카디널리티를 가진 변수를 확인해 보겠습니다.



```python
# check for cardinality in categorical variables

for var in categorical:
    
    print(var, ' contains ', len(df[var].unique()), ' labels')
```

<pre>
Date  contains  3436  labels
Location  contains  49  labels
WindGustDir  contains  17  labels
WindDir9am  contains  17  labels
WindDir3pm  contains  17  labels
RainToday  contains  3  labels
RainTomorrow  contains  3  labels
</pre>
날짜(Date) 변수가 전처리(preprocessing) 되어야 한다는 것을 알 수 있습니다. 다음 섹션에서 전처리를 수행할 것입니다.



다른 변수들은 비교적 적은 수의 변수들을 포함하고 있습니다.


### Feature Engineering of Date Variable



```python
df['Date'].dtypes
```

<pre>
dtype('O')
</pre>
데이터셋에서 Date 변수의 데이터 타입이 object로 표시되어 있습니다. 이 변수를 datetime 형식으로 변환할 것입니다. 이렇게 함으로써 날짜와 관련된 작업을 더 쉽게 수행할 수 있습니다.



```python
# parse the dates, currently coded as strings, into datetime format

df['Date'] = pd.to_datetime(df['Date'])
```


```python
# extract year from date

df['Year'] = df['Date'].dt.year

df['Year'].head()
```

<pre>
0    2008
1    2008
2    2008
3    2008
4    2008
Name: Year, dtype: int64
</pre>

```python
# extract month from date

df['Month'] = df['Date'].dt.month

df['Month'].head()
```

<pre>
0    12
1    12
2    12
3    12
4    12
Name: Month, dtype: int64
</pre>

```python
# extract day from date

df['Day'] = df['Date'].dt.day

df['Day'].head()
```

<pre>
0    1
1    2
2    3
3    4
4    5
Name: Day, dtype: int64
</pre>

```python
# again view the summary of dataset

df.info()
```

<pre>
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 145460 entries, 0 to 145459
Data columns (total 26 columns):
Date             145460 non-null datetime64[ns]
Location         145460 non-null object
MinTemp          143975 non-null float64
MaxTemp          144199 non-null float64
Rainfall         142199 non-null float64
Evaporation      82670 non-null float64
Sunshine         75625 non-null float64
WindGustDir      135134 non-null object
WindGustSpeed    135197 non-null float64
WindDir9am       134894 non-null object
WindDir3pm       141232 non-null object
WindSpeed9am     143693 non-null float64
WindSpeed3pm     142398 non-null float64
Humidity9am      142806 non-null float64
Humidity3pm      140953 non-null float64
Pressure9am      130395 non-null float64
Pressure3pm      130432 non-null float64
Cloud9am         89572 non-null float64
Cloud3pm         86102 non-null float64
Temp9am          143693 non-null float64
Temp3pm          141851 non-null float64
RainToday        142199 non-null object
RainTomorrow     142193 non-null object
Year             145460 non-null int64
Month            145460 non-null int64
Day              145460 non-null int64
dtypes: datetime64[ns](1), float64(16), int64(3), object(6)
memory usage: 28.9+ MB
</pre>
Date 변수에서 세 개의 추가적인 열이 생성되었습니다. 이제 원래의 Date 변수를 데이터셋에서 삭제하도록 하겠습니다.



```python
# drop the original Date variable

df.drop('Date', axis=1, inplace = True)
```


```python
# preview the dataset again

df.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Location</th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustDir</th>
      <th>WindGustSpeed</th>
      <th>WindDir9am</th>
      <th>WindDir3pm</th>
      <th>...</th>
      <th>Pressure3pm</th>
      <th>Cloud9am</th>
      <th>Cloud3pm</th>
      <th>Temp9am</th>
      <th>Temp3pm</th>
      <th>RainToday</th>
      <th>RainTomorrow</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Albury</td>
      <td>13.4</td>
      <td>22.9</td>
      <td>0.6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>W</td>
      <td>44.0</td>
      <td>W</td>
      <td>WNW</td>
      <td>...</td>
      <td>1007.1</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>16.9</td>
      <td>21.8</td>
      <td>No</td>
      <td>No</td>
      <td>2008</td>
      <td>12</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albury</td>
      <td>7.4</td>
      <td>25.1</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WNW</td>
      <td>44.0</td>
      <td>NNW</td>
      <td>WSW</td>
      <td>...</td>
      <td>1007.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>17.2</td>
      <td>24.3</td>
      <td>No</td>
      <td>No</td>
      <td>2008</td>
      <td>12</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Albury</td>
      <td>12.9</td>
      <td>25.7</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WSW</td>
      <td>46.0</td>
      <td>W</td>
      <td>WSW</td>
      <td>...</td>
      <td>1008.7</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>21.0</td>
      <td>23.2</td>
      <td>No</td>
      <td>No</td>
      <td>2008</td>
      <td>12</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Albury</td>
      <td>9.2</td>
      <td>28.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NE</td>
      <td>24.0</td>
      <td>SE</td>
      <td>E</td>
      <td>...</td>
      <td>1012.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18.1</td>
      <td>26.5</td>
      <td>No</td>
      <td>No</td>
      <td>2008</td>
      <td>12</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Albury</td>
      <td>17.5</td>
      <td>32.3</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>W</td>
      <td>41.0</td>
      <td>ENE</td>
      <td>NW</td>
      <td>...</td>
      <td>1006.0</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>17.8</td>
      <td>29.7</td>
      <td>No</td>
      <td>No</td>
      <td>2008</td>
      <td>12</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>


### Explore Categorical Variables





Now, I will explore the categorical variables one by one. 



```python
# find categorical variables

categorical = [var for var in df.columns if df[var].dtype=='O']

print('There are {} categorical variables\n'.format(len(categorical)))

print('The categorical variables are :', categorical)
```

<pre>
There are 6 categorical variables

The categorical variables are : ['Location', 'WindGustDir', 'WindDir9am', 'WindDir3pm', 'RainToday', 'RainTomorrow']
</pre>
해당 데이터셋에는 총 6개의 범주형 변수가 있습니다. Date 변수는 제거되었습니다. 먼저 범주형 변수에서 결측값이 있는지 확인해보겠습니다.



```python
# check for missing values in categorical variables 

df[categorical].isnull().sum()
```

<pre>
Location            0
WindGustDir     10326
WindDir9am      10566
WindDir3pm       4228
RainToday        3261
RainTomorrow     3267
dtype: int64
</pre>
### Explore `Location` variable



```python
# print number of labels in Location variable

print('Location contains', len(df.Location.unique()), 'labels')
```

<pre>
Location contains 49 labels
</pre>

```python
# check labels in location variable

df.Location.unique()
```

<pre>
array(['Albury', 'BadgerysCreek', 'Cobar', 'CoffsHarbour', 'Moree',
       'Newcastle', 'NorahHead', 'NorfolkIsland', 'Penrith', 'Richmond',
       'Sydney', 'SydneyAirport', 'WaggaWagga', 'Williamtown',
       'Wollongong', 'Canberra', 'Tuggeranong', 'MountGinini', 'Ballarat',
       'Bendigo', 'Sale', 'MelbourneAirport', 'Melbourne', 'Mildura',
       'Nhil', 'Portland', 'Watsonia', 'Dartmoor', 'Brisbane', 'Cairns',
       'GoldCoast', 'Townsville', 'Adelaide', 'MountGambier', 'Nuriootpa',
       'Woomera', 'Albany', 'Witchcliffe', 'PearceRAAF', 'PerthAirport',
       'Perth', 'SalmonGums', 'Walpole', 'Hobart', 'Launceston',
       'AliceSprings', 'Darwin', 'Katherine', 'Uluru'], dtype=object)
</pre>

```python
# check frequency distribution of values in Location variable

df.Location.value_counts()
```

<pre>
Canberra            3436
Sydney              3344
Brisbane            3193
Perth               3193
Adelaide            3193
Hobart              3193
Melbourne           3193
Darwin              3193
Ballarat            3040
Cairns              3040
Townsville          3040
MountGinini         3040
MountGambier        3040
Albury              3040
Bendigo             3040
AliceSprings        3040
GoldCoast           3040
Launceston          3040
Albany              3040
Wollongong          3040
Newcastle           3039
Penrith             3039
Tuggeranong         3039
Witchcliffe         3009
NorfolkIsland       3009
CoffsHarbour        3009
MelbourneAirport    3009
PerthAirport        3009
Moree               3009
SydneyAirport       3009
Williamtown         3009
Portland            3009
PearceRAAF          3009
Watsonia            3009
Nuriootpa           3009
WaggaWagga          3009
Mildura             3009
Richmond            3009
Cobar               3009
Sale                3009
Dartmoor            3009
Woomera             3009
BadgerysCreek       3009
Walpole             3006
NorahHead           3004
SalmonGums          3001
Uluru               1578
Nhil                1578
Katherine           1578
Name: Location, dtype: int64
</pre>

```python
# let's do One Hot Encoding of Location variable
# get k-1 dummy variables after One Hot Encoding 
# preview the dataset with head() method

pd.get_dummies(df.Location, drop_first=True).head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Albany</th>
      <th>Albury</th>
      <th>AliceSprings</th>
      <th>BadgerysCreek</th>
      <th>Ballarat</th>
      <th>Bendigo</th>
      <th>Brisbane</th>
      <th>Cairns</th>
      <th>Canberra</th>
      <th>Cobar</th>
      <th>...</th>
      <th>Townsville</th>
      <th>Tuggeranong</th>
      <th>Uluru</th>
      <th>WaggaWagga</th>
      <th>Walpole</th>
      <th>Watsonia</th>
      <th>Williamtown</th>
      <th>Witchcliffe</th>
      <th>Wollongong</th>
      <th>Woomera</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 48 columns</p>
</div>


### Explore `WindGustDir` variable



```python
# print number of labels in WindGustDir variable

print('WindGustDir contains', len(df['WindGustDir'].unique()), 'labels')
```

<pre>
WindGustDir contains 17 labels
</pre>

```python
# check labels in WindGustDir variable

df['WindGustDir'].unique()
```

<pre>
array(['W', 'WNW', 'WSW', 'NE', 'NNW', 'N', 'NNE', 'SW', nan, 'ENE',
       'SSE', 'S', 'NW', 'SE', 'ESE', 'E', 'SSW'], dtype=object)
</pre>

```python
# check frequency distribution of values in WindGustDir variable

df.WindGustDir.value_counts()
```

<pre>
W      9915
SE     9418
N      9313
SSE    9216
E      9181
S      9168
WSW    9069
SW     8967
SSW    8736
WNW    8252
NW     8122
ENE    8104
ESE    7372
NE     7133
NNW    6620
NNE    6548
Name: WindGustDir, dtype: int64
</pre>

```python
# let's do One Hot Encoding of WindGustDir variable
# get k-1 dummy variables after One Hot Encoding 
# also add an additional dummy variable to indicate there was missing data
# preview the dataset with head() method

pd.get_dummies(df.WindGustDir, drop_first=True, dummy_na=True).head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENE</th>
      <th>ESE</th>
      <th>N</th>
      <th>NE</th>
      <th>NNE</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
      <th>NaN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



```python
# sum the number of 1s per boolean variable over the rows of the dataset
# it will tell us how many observations we have for each category

pd.get_dummies(df.WindGustDir, drop_first=True, dummy_na=True).sum(axis=0)
```

<pre>
ENE     8104
ESE     7372
N       9313
NE      7133
NNE     6548
NNW     6620
NW      8122
S       9168
SE      9418
SSE     9216
SSW     8736
SW      8967
W       9915
WNW     8252
WSW     9069
NaN    10326
dtype: int64
</pre>
WindGustDir 변수에는 10326개의 결측치가 있다는 것을 확인할 수 있습니다.


### Explore `WindDir9am` variable



```python
# print number of labels in WindDir9am variable

print('WindDir9am contains', len(df['WindDir9am'].unique()), 'labels')
```

<pre>
WindDir9am contains 17 labels
</pre>

```python
# check labels in WindDir9am variable

df['WindDir9am'].unique()
```

<pre>
array(['W', 'NNW', 'SE', 'ENE', 'SW', 'SSE', 'S', 'NE', nan, 'SSW', 'N',
       'WSW', 'ESE', 'E', 'NW', 'WNW', 'NNE'], dtype=object)
</pre>

```python
# check frequency distribution of values in WindDir9am variable

df['WindDir9am'].value_counts()
```

<pre>
N      11758
SE      9287
E       9176
SSE     9112
NW      8749
S       8659
W       8459
SW      8423
NNE     8129
NNW     7980
ENE     7836
NE      7671
ESE     7630
SSW     7587
WNW     7414
WSW     7024
Name: WindDir9am, dtype: int64
</pre>

```python
# let's do One Hot Encoding of WindDir9am variable
# get k-1 dummy variables after One Hot Encoding 
# also add an additional dummy variable to indicate there was missing data
# preview the dataset with head() method

pd.get_dummies(df.WindDir9am, drop_first=True, dummy_na=True).head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENE</th>
      <th>ESE</th>
      <th>N</th>
      <th>NE</th>
      <th>NNE</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
      <th>NaN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



```python
# sum the number of 1s per boolean variable over the rows of the dataset
# it will tell us how many observations we have for each category

pd.get_dummies(df.WindDir9am, drop_first=True, dummy_na=True).sum(axis=0)
```

<pre>
ENE     7836
ESE     7630
N      11758
NE      7671
NNE     8129
NNW     7980
NW      8749
S       8659
SE      9287
SSE     9112
SSW     7587
SW      8423
W       8459
WNW     7414
WSW     7024
NaN    10566
dtype: int64
</pre>
WindDir9am 변수에는 10566개의 결측치가 있다는 것을 확인할 수 있습니다.


### Explore `WindDir3pm` variable



```python
# print number of labels in WindDir3pm variable

print('WindDir3pm contains', len(df['WindDir3pm'].unique()), 'labels')
```

<pre>
WindDir3pm contains 17 labels
</pre>

```python
# check labels in WindDir3pm variable

df['WindDir3pm'].unique()
```

<pre>
array(['WNW', 'WSW', 'E', 'NW', 'W', 'SSE', 'ESE', 'ENE', 'NNW', 'SSW',
       'SW', 'SE', 'N', 'S', 'NNE', nan, 'NE'], dtype=object)
</pre>

```python
# check frequency distribution of values in WindDir3pm variable

df['WindDir3pm'].value_counts()
```

<pre>
SE     10838
W      10110
S       9926
WSW     9518
SSE     9399
SW      9354
N       8890
WNW     8874
NW      8610
ESE     8505
E       8472
NE      8263
SSW     8156
NNW     7870
ENE     7857
NNE     6590
Name: WindDir3pm, dtype: int64
</pre>

```python
# let's do One Hot Encoding of WindDir3pm variable
# get k-1 dummy variables after One Hot Encoding 
# also add an additional dummy variable to indicate there was missing data
# preview the dataset with head() method

pd.get_dummies(df.WindDir3pm, drop_first=True, dummy_na=True).head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENE</th>
      <th>ESE</th>
      <th>N</th>
      <th>NE</th>
      <th>NNE</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
      <th>NaN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



```python
# sum the number of 1s per boolean variable over the rows of the dataset
# it will tell us how many observations we have for each category

pd.get_dummies(df.WindDir3pm, drop_first=True, dummy_na=True).sum(axis=0)
```

<pre>
ENE     7857
ESE     8505
N       8890
NE      8263
NNE     6590
NNW     7870
NW      8610
S       9926
SE     10838
SSE     9399
SSW     8156
SW      9354
W      10110
WNW     8874
WSW     9518
NaN     4228
dtype: int64
</pre>
WindDir3pm 변수에는 4228개의 결측치가 있다는 것을 확인할 수 있습니다.


### Explore `RainToday` variable



```python
# print number of labels in RainToday variable

print('RainToday contains', len(df['RainToday'].unique()), 'labels')
```

<pre>
RainToday contains 3 labels
</pre>

```python
# check labels in WindGustDir variable

df['RainToday'].unique()
```

<pre>
array(['No', 'Yes', nan], dtype=object)
</pre>

```python
# check frequency distribution of values in WindGustDir variable

df.RainToday.value_counts()
```

<pre>
No     110319
Yes     31880
Name: RainToday, dtype: int64
</pre>

```python
# let's do One Hot Encoding of RainToday variable
# get k-1 dummy variables after One Hot Encoding 
# also add an additional dummy variable to indicate there was missing data
# preview the dataset with head() method

pd.get_dummies(df.RainToday, drop_first=True, dummy_na=True).head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Yes</th>
      <th>NaN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



```python
# sum the number of 1s per boolean variable over the rows of the dataset
# it will tell us how many observations we have for each category

pd.get_dummies(df.RainToday, drop_first=True, dummy_na=True).sum(axis=0)
```

<pre>
Yes    31880
NaN     3261
dtype: int64
</pre>
RainToday 변수에는 3261개의 결측치가 있다는 것을 확인할 수 있습니다.


### Explore Numerical Variables



```python
# find numerical variables

numerical = [var for var in df.columns if df[var].dtype!='O']

print('There are {} numerical variables\n'.format(len(numerical)))

print('The numerical variables are :', numerical)
```

<pre>
There are 19 numerical variables

The numerical variables are : ['MinTemp', 'MaxTemp', 'Rainfall', 'Evaporation', 'Sunshine', 'WindGustSpeed', 'WindSpeed9am', 'WindSpeed3pm', 'Humidity9am', 'Humidity3pm', 'Pressure9am', 'Pressure3pm', 'Cloud9am', 'Cloud3pm', 'Temp9am', 'Temp3pm', 'Year', 'Month', 'Day']
</pre>

```python
# view the numerical variables

df[numerical].head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>Pressure9am</th>
      <th>Pressure3pm</th>
      <th>Cloud9am</th>
      <th>Cloud3pm</th>
      <th>Temp9am</th>
      <th>Temp3pm</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13.4</td>
      <td>22.9</td>
      <td>0.6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>44.0</td>
      <td>20.0</td>
      <td>24.0</td>
      <td>71.0</td>
      <td>22.0</td>
      <td>1007.7</td>
      <td>1007.1</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>16.9</td>
      <td>21.8</td>
      <td>2008</td>
      <td>12</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.4</td>
      <td>25.1</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>44.0</td>
      <td>4.0</td>
      <td>22.0</td>
      <td>44.0</td>
      <td>25.0</td>
      <td>1010.6</td>
      <td>1007.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>17.2</td>
      <td>24.3</td>
      <td>2008</td>
      <td>12</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12.9</td>
      <td>25.7</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>46.0</td>
      <td>19.0</td>
      <td>26.0</td>
      <td>38.0</td>
      <td>30.0</td>
      <td>1007.6</td>
      <td>1008.7</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>21.0</td>
      <td>23.2</td>
      <td>2008</td>
      <td>12</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.2</td>
      <td>28.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>24.0</td>
      <td>11.0</td>
      <td>9.0</td>
      <td>45.0</td>
      <td>16.0</td>
      <td>1017.6</td>
      <td>1012.8</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18.1</td>
      <td>26.5</td>
      <td>2008</td>
      <td>12</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.5</td>
      <td>32.3</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>41.0</td>
      <td>7.0</td>
      <td>20.0</td>
      <td>82.0</td>
      <td>33.0</td>
      <td>1010.8</td>
      <td>1006.0</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>17.8</td>
      <td>29.7</td>
      <td>2008</td>
      <td>12</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>


### Summary of numerical variables





- 16개의 숫자형 변수가 있습니다.

- 이들은 MinTemp, MaxTemp, Rainfall, Evaporation, Sunshine, WindGustSpeed, WindSpeed9am, WindSpeed3pm, Humidity9am, Humidity3pm, Pressure9am, Pressure3pm, Cloud9am, Cloud3pm, Temp9am 및 Temp3pm입니다.

- 이 모든 숫자형 변수는 연속형입니다.


## Explore problems within numerical variables





Now, I will explore the numerical variables.





### Missing values in numerical variables



```python
# check missing values in numerical variables

df[numerical].isnull().sum()
```

<pre>
MinTemp           1485
MaxTemp           1261
Rainfall          3261
Evaporation      62790
Sunshine         69835
WindGustSpeed    10263
WindSpeed9am      1767
WindSpeed3pm      3062
Humidity9am       2654
Humidity3pm       4507
Pressure9am      15065
Pressure3pm      15028
Cloud9am         55888
Cloud3pm         59358
Temp9am           1767
Temp3pm           3609
Year                 0
Month                0
Day                  0
dtype: int64
</pre>
총 16개의 수치형 특성들이 결측값이 있다는 것을 확인할 수 있습니다.


### Outliers in numerical variables



```python
# view summary statistics in numerical variables

print(round(df[numerical].describe()),2)
```

<pre>
        MinTemp   MaxTemp  Rainfall  Evaporation  Sunshine  WindGustSpeed  \
count  143975.0  144199.0  142199.0      82670.0   75625.0       135197.0   
mean       12.0      23.0       2.0          5.0       8.0           40.0   
std         6.0       7.0       8.0          4.0       4.0           14.0   
min        -8.0      -5.0       0.0          0.0       0.0            6.0   
25%         8.0      18.0       0.0          3.0       5.0           31.0   
50%        12.0      23.0       0.0          5.0       8.0           39.0   
75%        17.0      28.0       1.0          7.0      11.0           48.0   
max        34.0      48.0     371.0        145.0      14.0          135.0   

       WindSpeed9am  WindSpeed3pm  Humidity9am  Humidity3pm  Pressure9am  \
count      143693.0      142398.0     142806.0     140953.0     130395.0   
mean           14.0          19.0         69.0         52.0       1018.0   
std             9.0           9.0         19.0         21.0          7.0   
min             0.0           0.0          0.0          0.0        980.0   
25%             7.0          13.0         57.0         37.0       1013.0   
50%            13.0          19.0         70.0         52.0       1018.0   
75%            19.0          24.0         83.0         66.0       1022.0   
max           130.0          87.0        100.0        100.0       1041.0   

       Pressure3pm  Cloud9am  Cloud3pm   Temp9am   Temp3pm      Year  \
count     130432.0   89572.0   86102.0  143693.0  141851.0  145460.0   
mean        1015.0       4.0       5.0      17.0      22.0    2013.0   
std            7.0       3.0       3.0       6.0       7.0       3.0   
min          977.0       0.0       0.0      -7.0      -5.0    2007.0   
25%         1010.0       1.0       2.0      12.0      17.0    2011.0   
50%         1015.0       5.0       5.0      17.0      21.0    2013.0   
75%         1020.0       7.0       7.0      22.0      26.0    2015.0   
max         1040.0       9.0       9.0      40.0      47.0    2017.0   

          Month       Day  
count  145460.0  145460.0  
mean        6.0      16.0  
std         3.0       9.0  
min         1.0       1.0  
25%         3.0       8.0  
50%         6.0      16.0  
75%         9.0      23.0  
max        12.0      31.0   2
</pre>
`Rainfall`, `Evaporation`, `WindSpeed9am` , `WindSpeed3pm` 은 기본적으로 이상치를 포함하고 있는것으로 보입니다.



이를 시각화하기 위해 boxplot을 이용하도록 해봅니다.



```python
# draw boxplots to visualize outliers

plt.figure(figsize=(15,10))


plt.subplot(2, 2, 1)
fig = df.boxplot(column='Rainfall')
fig.set_title('')
fig.set_ylabel('Rainfall')


plt.subplot(2, 2, 2)
fig = df.boxplot(column='Evaporation')
fig.set_title('')
fig.set_ylabel('Evaporation')


plt.subplot(2, 2, 3)
fig = df.boxplot(column='WindSpeed9am')
fig.set_title('')
fig.set_ylabel('WindSpeed9am')


plt.subplot(2, 2, 4)
fig = df.boxplot(column='WindSpeed3pm')
fig.set_title('')
fig.set_ylabel('WindSpeed3pm')
```

<pre>
Text(0, 0.5, 'WindSpeed3pm')
</pre>
<img src="data:image/png;base64,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"/>

위 그래프를 통해 육안으로 보일 정도의 이상치가 있는 것이 확인되었습니다.


### Check the distribution of variables





이제 히스토그램을 그려서 분포를 확인하고 정규 분포인지 왜도(skewness)가 있는지 찾아보겠습니다. 변수가 정규 분포를 따른다면, 극단치 분석(Extreme Value Analysis)을 수행하겠습니다. 그러나 만약 왜도가 있다면, IQR(Interquantile range)을 찾아보겠습니다.



```python
# plot histogram to check distribution

plt.figure(figsize=(15,10))


plt.subplot(2, 2, 1)
fig = df.Rainfall.hist(bins=10)
fig.set_xlabel('Rainfall')
fig.set_ylabel('RainTomorrow')


plt.subplot(2, 2, 2)
fig = df.Evaporation.hist(bins=10)
fig.set_xlabel('Evaporation')
fig.set_ylabel('RainTomorrow')


plt.subplot(2, 2, 3)
fig = df.WindSpeed9am.hist(bins=10)
fig.set_xlabel('WindSpeed9am')
fig.set_ylabel('RainTomorrow')


plt.subplot(2, 2, 4)
fig = df.WindSpeed3pm.hist(bins=10)
fig.set_xlabel('WindSpeed3pm')
fig.set_ylabel('RainTomorrow')
```

<pre>
Text(0, 0.5, 'RainTomorrow')
</pre>
<img src="data:image/png;base64,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"/>

모든 네 개의 변수가 비대칭이라는 것을 알 수 있습니다. 따라서, 이상치를 찾기 위해 사분위범위를 사용할 것입니다.










```python
# find outliers for Rainfall variable

IQR = df.Rainfall.quantile(0.75) - df.Rainfall.quantile(0.25)
Lower_fence = df.Rainfall.quantile(0.25) - (IQR * 3)
Upper_fence = df.Rainfall.quantile(0.75) + (IQR * 3)
print('Rainfall outliers are values < {lowerboundary} or > {upperboundary}'.format(lowerboundary=Lower_fence, upperboundary=Upper_fence))
```

<pre>
Rainfall outliers are values < -2.4000000000000004 or > 3.2
</pre>
Rainfall 변수에서 최소값은 0.0이고, 최대값은 371.0입니다. 따라서, 이상치는 3.2보다 큰 값입니다.



```python
# find outliers for Evaporation variable

IQR = df.Evaporation.quantile(0.75) - df.Evaporation.quantile(0.25)
Lower_fence = df.Evaporation.quantile(0.25) - (IQR * 3)
Upper_fence = df.Evaporation.quantile(0.75) + (IQR * 3)
print('Evaporation outliers are values < {lowerboundary} or > {upperboundary}'.format(lowerboundary=Lower_fence, upperboundary=Upper_fence))
```

<pre>
Evaporation outliers are values < -11.800000000000002 or > 21.800000000000004
</pre>
Evaporation 변수에서 최소값과 최대값은 각각 0.0과 145.0입니다. 이상치는 21.8보다 큰 값입니다.



```python
# find outliers for WindSpeed9am variable

IQR = df.WindSpeed9am.quantile(0.75) - df.WindSpeed9am.quantile(0.25)
Lower_fence = df.WindSpeed9am.quantile(0.25) - (IQR * 3)
Upper_fence = df.WindSpeed9am.quantile(0.75) + (IQR * 3)
print('WindSpeed9am outliers are values < {lowerboundary} or > {upperboundary}'.format(lowerboundary=Lower_fence, upperboundary=Upper_fence))
```

<pre>
WindSpeed9am outliers are values < -29.0 or > 55.0
</pre>
WindSpeed9am 변수에서 최소값과 최대값은 각각 0.0과 130.0입니다. 따라서, 이상치는 55.0보다 큰 값입니다.



```python
# find outliers for WindSpeed3pm variable

IQR = df.WindSpeed3pm.quantile(0.75) - df.WindSpeed3pm.quantile(0.25)
Lower_fence = df.WindSpeed3pm.quantile(0.25) - (IQR * 3)
Upper_fence = df.WindSpeed3pm.quantile(0.75) + (IQR * 3)
print('WindSpeed3pm outliers are values < {lowerboundary} or > {upperboundary}'.format(lowerboundary=Lower_fence, upperboundary=Upper_fence))
```

<pre>
WindSpeed3pm outliers are values < -20.0 or > 57.0
</pre>
WindSpeed3pm 변수의 최소값과 최대값은 각각 0.0과 87.0입니다. 이상치는 값이 57.0보다 큰 경우입니다.


# **8. Declare feature vector and target variable** <a class="anchor" id="8"></a>





[Table of Contents](#0.1)



```python
X = df.drop(['RainTomorrow'], axis=1)

y = df['RainTomorrow']
```

# **9. Split data into separate training and test set** <a class="anchor" id="9"></a>





[Table of Contents](#0.1)



```python
# split X and y into training and testing sets

from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 0)
```


```python
# check the shape of X_train and X_test

X_train.shape, X_test.shape
```

<pre>
((116368, 24), (29092, 24))
</pre>
# **10. Feature Engineering** <a class="anchor" id="10"></a>





[Table of Contents](#0.1)





특성 엔지니어링은 원시 데이터를 유용한 특성으로 변환하여 모델을 이해하고 예측 능력을 높이는 과정입니다. 다른 유형의 변수에 대해 특성 엔지니어링을 수행할 것입니다.



먼저, 범주형 및 수치 변수를 다시 별도로 표시하겠습니다.



```python
# check data types in X_train

X_train.dtypes
```

<pre>
Location          object
MinTemp          float64
MaxTemp          float64
Rainfall         float64
Evaporation      float64
Sunshine         float64
WindGustDir       object
WindGustSpeed    float64
WindDir9am        object
WindDir3pm        object
WindSpeed9am     float64
WindSpeed3pm     float64
Humidity9am      float64
Humidity3pm      float64
Pressure9am      float64
Pressure3pm      float64
Cloud9am         float64
Cloud3pm         float64
Temp9am          float64
Temp3pm          float64
RainToday         object
Year               int64
Month              int64
Day                int64
dtype: object
</pre>

```python
# display categorical variables

categorical = [col for col in X_train.columns if X_train[col].dtypes == 'O']

categorical
```

<pre>
['Location', 'WindGustDir', 'WindDir9am', 'WindDir3pm', 'RainToday']
</pre>

```python
# display numerical variables

numerical = [col for col in X_train.columns if X_train[col].dtypes != 'O']

numerical
```

<pre>
['MinTemp',
 'MaxTemp',
 'Rainfall',
 'Evaporation',
 'Sunshine',
 'WindGustSpeed',
 'WindSpeed9am',
 'WindSpeed3pm',
 'Humidity9am',
 'Humidity3pm',
 'Pressure9am',
 'Pressure3pm',
 'Cloud9am',
 'Cloud3pm',
 'Temp9am',
 'Temp3pm',
 'Year',
 'Month',
 'Day']
</pre>
### Engineering missing values in numerical variables






```python
# check missing values in numerical variables in X_train

X_train[numerical].isnull().sum()
```

<pre>
MinTemp           1183
MaxTemp           1019
Rainfall          2617
Evaporation      50355
Sunshine         55899
WindGustSpeed     8218
WindSpeed9am      1409
WindSpeed3pm      2456
Humidity9am       2147
Humidity3pm       3598
Pressure9am      12091
Pressure3pm      12064
Cloud9am         44796
Cloud3pm         47557
Temp9am           1415
Temp3pm           2865
Year                 0
Month                0
Day                  0
dtype: int64
</pre>

```python
# check missing values in numerical variables in X_test

X_test[numerical].isnull().sum()
```

<pre>
MinTemp            302
MaxTemp            242
Rainfall           644
Evaporation      12435
Sunshine         13936
WindGustSpeed     2045
WindSpeed9am       358
WindSpeed3pm       606
Humidity9am        507
Humidity3pm        909
Pressure9am       2974
Pressure3pm       2964
Cloud9am         11092
Cloud3pm         11801
Temp9am            352
Temp3pm            744
Year                 0
Month                0
Day                  0
dtype: int64
</pre>

```python
# print percentage of missing values in the numerical variables in training set

for col in numerical:
    if X_train[col].isnull().mean()>0:
        print(col, round(X_train[col].isnull().mean(),4))
```

<pre>
MinTemp 0.0102
MaxTemp 0.0088
Rainfall 0.0225
Evaporation 0.4327
Sunshine 0.4804
WindGustSpeed 0.0706
WindSpeed9am 0.0121
WindSpeed3pm 0.0211
Humidity9am 0.0185
Humidity3pm 0.0309
Pressure9am 0.1039
Pressure3pm 0.1037
Cloud9am 0.385
Cloud3pm 0.4087
Temp9am 0.0122
Temp3pm 0.0246
</pre>
### Assumption





데이터가 완전히 무작위로 누락되었다고 가정합니다 (MCAR). 누락된 값 채우기에는 두 가지 방법이 있습니다. 평균 또는 중앙값 채우기와 무작위 샘플 채우기입니다. 데이터 세트에 이상치가 있을 때 중앙값 채우기를 사용해야 합니다. 이에 따라 중앙값 채우기를 사용할 것입니다. 중앙값 채우기는 이상치에 강건합니다.



누락된 값을 데이터의 적절한 통계 측정치인 중앙값으로 대체할 것입니다. 대체는 학습 세트에서 수행되어야 하며, 그 후에 테스트 세트로 전파됩니다. 즉, 학습 및 테스트 세트 모두에서 누락된 값을 채우기 위해 사용할 통계 측정치는 학습 세트에서만 추출해야 합니다. 이는 과적합을 방지하기 위함입니다.



```python
# impute missing values in X_train and X_test with respective column median in X_train

for df1 in [X_train, X_test]:
    for col in numerical:
        col_median=X_train[col].median()
        df1[col].fillna(col_median, inplace=True)           
      
```


```python
# check again missing values in numerical variables in X_train

X_train[numerical].isnull().sum()
```

<pre>
MinTemp          0
MaxTemp          0
Rainfall         0
Evaporation      0
Sunshine         0
WindGustSpeed    0
WindSpeed9am     0
WindSpeed3pm     0
Humidity9am      0
Humidity3pm      0
Pressure9am      0
Pressure3pm      0
Cloud9am         0
Cloud3pm         0
Temp9am          0
Temp3pm          0
Year             0
Month            0
Day              0
dtype: int64
</pre>

```python
# check missing values in numerical variables in X_test

X_test[numerical].isnull().sum()
```

<pre>
MinTemp          0
MaxTemp          0
Rainfall         0
Evaporation      0
Sunshine         0
WindGustSpeed    0
WindSpeed9am     0
WindSpeed3pm     0
Humidity9am      0
Humidity3pm      0
Pressure9am      0
Pressure3pm      0
Cloud9am         0
Cloud3pm         0
Temp9am          0
Temp3pm          0
Year             0
Month            0
Day              0
dtype: int64
</pre>
이제 수치형 변수들에는 결측치가 없도록 만들었습니다.


### Engineering missing values in categorical variables



```python
# print percentage of missing values in the categorical variables in training set

X_train[categorical].isnull().mean()
```

<pre>
Location       0.000000
WindGustDir    0.071068
WindDir9am     0.072597
WindDir3pm     0.028951
RainToday      0.022489
dtype: float64
</pre>

```python
# print categorical variables with missing data

for col in categorical:
    if X_train[col].isnull().mean()>0:
        print(col, (X_train[col].isnull().mean()))
```

<pre>
WindGustDir 0.07106764746322013
WindDir9am 0.07259727760208992
WindDir3pm 0.028951258077822083
RainToday 0.02248900041248453
</pre>

```python
# impute missing categorical variables with most frequent value

for df2 in [X_train, X_test]:
    df2['WindGustDir'].fillna(X_train['WindGustDir'].mode()[0], inplace=True)
    df2['WindDir9am'].fillna(X_train['WindDir9am'].mode()[0], inplace=True)
    df2['WindDir3pm'].fillna(X_train['WindDir3pm'].mode()[0], inplace=True)
    df2['RainToday'].fillna(X_train['RainToday'].mode()[0], inplace=True)
```


```python
# check missing values in categorical variables in X_train

X_train[categorical].isnull().sum()
```

<pre>
Location       0
WindGustDir    0
WindDir9am     0
WindDir3pm     0
RainToday      0
dtype: int64
</pre>

```python
# check missing values in categorical variables in X_test

X_test[categorical].isnull().sum()
```

<pre>
Location       0
WindGustDir    0
WindDir9am     0
WindDir3pm     0
RainToday      0
dtype: int64
</pre>
즉 최빈값으로 범주형의 결측치들을 처리했습니다.


이제 최종적으로 점검해봅니다.



```python
# check missing values in X_train

X_train.isnull().sum()
```

<pre>
Location         0
MinTemp          0
MaxTemp          0
Rainfall         0
Evaporation      0
Sunshine         0
WindGustDir      0
WindGustSpeed    0
WindDir9am       0
WindDir3pm       0
WindSpeed9am     0
WindSpeed3pm     0
Humidity9am      0
Humidity3pm      0
Pressure9am      0
Pressure3pm      0
Cloud9am         0
Cloud3pm         0
Temp9am          0
Temp3pm          0
RainToday        0
Year             0
Month            0
Day              0
dtype: int64
</pre>

```python
# check missing values in X_test

X_test.isnull().sum()
```

<pre>
Location         0
MinTemp          0
MaxTemp          0
Rainfall         0
Evaporation      0
Sunshine         0
WindGustDir      0
WindGustSpeed    0
WindDir9am       0
WindDir3pm       0
WindSpeed9am     0
WindSpeed3pm     0
Humidity9am      0
Humidity3pm      0
Pressure9am      0
Pressure3pm      0
Cloud9am         0
Cloud3pm         0
Temp9am          0
Temp3pm          0
RainToday        0
Year             0
Month            0
Day              0
dtype: int64
</pre>
We can see that there are no missing values in X_train and X_test.


### Engineering outliers in numerical variables





Rainfall, Evaporation, WindSpeed9am 및 WindSpeed3pm 열에 이상치(outliers)가 포함되어 있는 것으로 확인되었습니다. 이상치를 제거하기 위해 상한선(top-coding) 접근법을 사용하여 최대값을 제한하겠습니다.



```python
def max_value(df3, variable, top):
    return np.where(df3[variable]>top, top, df3[variable])

for df3 in [X_train, X_test]:
    df3['Rainfall'] = max_value(df3, 'Rainfall', 3.2)
    df3['Evaporation'] = max_value(df3, 'Evaporation', 21.8)
    df3['WindSpeed9am'] = max_value(df3, 'WindSpeed9am', 55)
    df3['WindSpeed3pm'] = max_value(df3, 'WindSpeed3pm', 57)
```


```python
X_train.Rainfall.max(), X_test.Rainfall.max()
```

<pre>
(3.2, 3.2)
</pre>

```python
X_train.Evaporation.max(), X_test.Evaporation.max()
```

<pre>
(21.8, 21.8)
</pre>

```python
X_train.WindSpeed9am.max(), X_test.WindSpeed9am.max()
```

<pre>
(55.0, 55.0)
</pre>

```python
X_train.WindSpeed3pm.max(), X_test.WindSpeed3pm.max()
```

<pre>
(57.0, 57.0)
</pre>

```python
X_train[numerical].describe()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>Pressure9am</th>
      <th>Pressure3pm</th>
      <th>Cloud9am</th>
      <th>Cloud3pm</th>
      <th>Temp9am</th>
      <th>Temp3pm</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>12.190189</td>
      <td>23.203107</td>
      <td>0.670800</td>
      <td>5.093362</td>
      <td>7.982476</td>
      <td>39.982091</td>
      <td>14.029381</td>
      <td>18.687466</td>
      <td>68.950691</td>
      <td>51.605828</td>
      <td>1017.639891</td>
      <td>1015.244946</td>
      <td>4.664092</td>
      <td>4.710728</td>
      <td>16.979454</td>
      <td>21.657195</td>
      <td>2012.767058</td>
      <td>6.395091</td>
      <td>15.731954</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6.366893</td>
      <td>7.085408</td>
      <td>1.181512</td>
      <td>2.800200</td>
      <td>2.761639</td>
      <td>13.127953</td>
      <td>8.835596</td>
      <td>8.700618</td>
      <td>18.811437</td>
      <td>20.439999</td>
      <td>6.728234</td>
      <td>6.661517</td>
      <td>2.280687</td>
      <td>2.106040</td>
      <td>6.449641</td>
      <td>6.848293</td>
      <td>2.538401</td>
      <td>3.425451</td>
      <td>8.796931</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-8.500000</td>
      <td>-4.800000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>6.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>980.500000</td>
      <td>977.100000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-7.200000</td>
      <td>-5.400000</td>
      <td>2007.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.700000</td>
      <td>18.000000</td>
      <td>0.000000</td>
      <td>4.000000</td>
      <td>8.200000</td>
      <td>31.000000</td>
      <td>7.000000</td>
      <td>13.000000</td>
      <td>57.000000</td>
      <td>37.000000</td>
      <td>1013.500000</td>
      <td>1011.100000</td>
      <td>3.000000</td>
      <td>4.000000</td>
      <td>12.300000</td>
      <td>16.700000</td>
      <td>2011.000000</td>
      <td>3.000000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>12.000000</td>
      <td>22.600000</td>
      <td>0.000000</td>
      <td>4.700000</td>
      <td>8.400000</td>
      <td>39.000000</td>
      <td>13.000000</td>
      <td>19.000000</td>
      <td>70.000000</td>
      <td>52.000000</td>
      <td>1017.600000</td>
      <td>1015.200000</td>
      <td>5.000000</td>
      <td>5.000000</td>
      <td>16.700000</td>
      <td>21.100000</td>
      <td>2013.000000</td>
      <td>6.000000</td>
      <td>16.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>16.800000</td>
      <td>28.200000</td>
      <td>0.600000</td>
      <td>5.200000</td>
      <td>8.600000</td>
      <td>46.000000</td>
      <td>19.000000</td>
      <td>24.000000</td>
      <td>83.000000</td>
      <td>65.000000</td>
      <td>1021.800000</td>
      <td>1019.400000</td>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>21.500000</td>
      <td>26.200000</td>
      <td>2015.000000</td>
      <td>9.000000</td>
      <td>23.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>31.900000</td>
      <td>48.100000</td>
      <td>3.200000</td>
      <td>21.800000</td>
      <td>14.500000</td>
      <td>135.000000</td>
      <td>55.000000</td>
      <td>57.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>1041.000000</td>
      <td>1039.600000</td>
      <td>9.000000</td>
      <td>8.000000</td>
      <td>40.200000</td>
      <td>46.700000</td>
      <td>2017.000000</td>
      <td>12.000000</td>
      <td>31.000000</td>
    </tr>
  </tbody>
</table>
</div>


이제 Rainfall, Evaporation, WindSpeed9am 및 WindSpeed3pm 열의 이상값이 최댓값으로 제한되었습니다.


### Encode categorical variables



```python
categorical
```

<pre>
['Location', 'WindGustDir', 'WindDir9am', 'WindDir3pm', 'RainToday']
</pre>

```python
X_train[categorical].head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Location</th>
      <th>WindGustDir</th>
      <th>WindDir9am</th>
      <th>WindDir3pm</th>
      <th>RainToday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>22926</th>
      <td>NorfolkIsland</td>
      <td>ESE</td>
      <td>ESE</td>
      <td>ESE</td>
      <td>No</td>
    </tr>
    <tr>
      <th>80735</th>
      <td>Watsonia</td>
      <td>NE</td>
      <td>NNW</td>
      <td>NNE</td>
      <td>No</td>
    </tr>
    <tr>
      <th>121764</th>
      <td>Perth</td>
      <td>SW</td>
      <td>N</td>
      <td>SW</td>
      <td>Yes</td>
    </tr>
    <tr>
      <th>139821</th>
      <td>Darwin</td>
      <td>ESE</td>
      <td>ESE</td>
      <td>E</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1867</th>
      <td>Albury</td>
      <td>E</td>
      <td>ESE</td>
      <td>E</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>
</div>



```python
# encode RainToday variable

import category_encoders as ce

encoder = ce.BinaryEncoder(cols=['RainToday'])

X_train = encoder.fit_transform(X_train)

X_test = encoder.transform(X_test)
```

좀더 정확한 측정을 위해 RainToday 특성을 이진화합니다.



```python
X_train.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Location</th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustDir</th>
      <th>WindGustSpeed</th>
      <th>WindDir9am</th>
      <th>WindDir3pm</th>
      <th>...</th>
      <th>Pressure3pm</th>
      <th>Cloud9am</th>
      <th>Cloud3pm</th>
      <th>Temp9am</th>
      <th>Temp3pm</th>
      <th>RainToday_0</th>
      <th>RainToday_1</th>
      <th>Year</th>
      <th>Month</th>
      <th>Day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>22926</th>
      <td>NorfolkIsland</td>
      <td>18.8</td>
      <td>23.7</td>
      <td>0.2</td>
      <td>5.0</td>
      <td>7.3</td>
      <td>ESE</td>
      <td>52.0</td>
      <td>ESE</td>
      <td>ESE</td>
      <td>...</td>
      <td>1013.9</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>21.4</td>
      <td>22.2</td>
      <td>0</td>
      <td>1</td>
      <td>2014</td>
      <td>3</td>
      <td>12</td>
    </tr>
    <tr>
      <th>80735</th>
      <td>Watsonia</td>
      <td>9.3</td>
      <td>24.0</td>
      <td>0.2</td>
      <td>1.6</td>
      <td>10.9</td>
      <td>NE</td>
      <td>48.0</td>
      <td>NNW</td>
      <td>NNE</td>
      <td>...</td>
      <td>1014.6</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>14.3</td>
      <td>23.2</td>
      <td>0</td>
      <td>1</td>
      <td>2016</td>
      <td>10</td>
      <td>6</td>
    </tr>
    <tr>
      <th>121764</th>
      <td>Perth</td>
      <td>10.9</td>
      <td>22.2</td>
      <td>1.4</td>
      <td>1.2</td>
      <td>9.6</td>
      <td>SW</td>
      <td>26.0</td>
      <td>N</td>
      <td>SW</td>
      <td>...</td>
      <td>1014.9</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>16.6</td>
      <td>21.5</td>
      <td>1</td>
      <td>0</td>
      <td>2011</td>
      <td>8</td>
      <td>31</td>
    </tr>
    <tr>
      <th>139821</th>
      <td>Darwin</td>
      <td>19.3</td>
      <td>29.9</td>
      <td>0.0</td>
      <td>9.2</td>
      <td>11.0</td>
      <td>ESE</td>
      <td>43.0</td>
      <td>ESE</td>
      <td>E</td>
      <td>...</td>
      <td>1012.1</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>23.2</td>
      <td>29.1</td>
      <td>0</td>
      <td>1</td>
      <td>2010</td>
      <td>6</td>
      <td>11</td>
    </tr>
    <tr>
      <th>1867</th>
      <td>Albury</td>
      <td>15.7</td>
      <td>17.6</td>
      <td>3.2</td>
      <td>4.7</td>
      <td>8.4</td>
      <td>E</td>
      <td>20.0</td>
      <td>ESE</td>
      <td>E</td>
      <td>...</td>
      <td>1010.5</td>
      <td>8.0</td>
      <td>8.0</td>
      <td>16.5</td>
      <td>17.3</td>
      <td>1</td>
      <td>0</td>
      <td>2014</td>
      <td>4</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 25 columns</p>
</div>


이제 훈련셋을 만듭니다.



```python
X_train = pd.concat([X_train[numerical], X_train[['RainToday_0', 'RainToday_1']],
                     pd.get_dummies(X_train.Location), 
                     pd.get_dummies(X_train.WindGustDir),
                     pd.get_dummies(X_train.WindDir9am),
                     pd.get_dummies(X_train.WindDir3pm)], axis=1)
```


```python
X_train.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>...</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>22926</th>
      <td>18.8</td>
      <td>23.7</td>
      <td>0.2</td>
      <td>5.0</td>
      <td>7.3</td>
      <td>52.0</td>
      <td>31.0</td>
      <td>28.0</td>
      <td>74.0</td>
      <td>73.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>80735</th>
      <td>9.3</td>
      <td>24.0</td>
      <td>0.2</td>
      <td>1.6</td>
      <td>10.9</td>
      <td>48.0</td>
      <td>13.0</td>
      <td>24.0</td>
      <td>74.0</td>
      <td>55.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121764</th>
      <td>10.9</td>
      <td>22.2</td>
      <td>1.4</td>
      <td>1.2</td>
      <td>9.6</td>
      <td>26.0</td>
      <td>0.0</td>
      <td>11.0</td>
      <td>85.0</td>
      <td>47.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>139821</th>
      <td>19.3</td>
      <td>29.9</td>
      <td>0.0</td>
      <td>9.2</td>
      <td>11.0</td>
      <td>43.0</td>
      <td>26.0</td>
      <td>17.0</td>
      <td>44.0</td>
      <td>37.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1867</th>
      <td>15.7</td>
      <td>17.6</td>
      <td>3.2</td>
      <td>4.7</td>
      <td>8.4</td>
      <td>20.0</td>
      <td>11.0</td>
      <td>13.0</td>
      <td>100.0</td>
      <td>100.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 118 columns</p>
</div>


테스트셋 또한 똑같은 방식으로 만들어 줍니다.



```python
X_test = pd.concat([X_test[numerical], X_test[['RainToday_0', 'RainToday_1']],
                     pd.get_dummies(X_test.Location), 
                     pd.get_dummies(X_test.WindGustDir),
                     pd.get_dummies(X_test.WindDir9am),
                     pd.get_dummies(X_test.WindDir3pm)], axis=1)
```


```python
X_test.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>...</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>138175</th>
      <td>21.9</td>
      <td>39.4</td>
      <td>1.6</td>
      <td>11.2</td>
      <td>11.5</td>
      <td>57.0</td>
      <td>20.0</td>
      <td>33.0</td>
      <td>50.0</td>
      <td>26.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>38638</th>
      <td>20.5</td>
      <td>37.5</td>
      <td>0.0</td>
      <td>9.2</td>
      <td>8.4</td>
      <td>59.0</td>
      <td>17.0</td>
      <td>20.0</td>
      <td>47.0</td>
      <td>22.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>124058</th>
      <td>5.1</td>
      <td>17.2</td>
      <td>0.2</td>
      <td>4.7</td>
      <td>8.4</td>
      <td>50.0</td>
      <td>28.0</td>
      <td>22.0</td>
      <td>68.0</td>
      <td>51.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>99214</th>
      <td>11.9</td>
      <td>16.8</td>
      <td>1.0</td>
      <td>4.7</td>
      <td>8.4</td>
      <td>28.0</td>
      <td>11.0</td>
      <td>13.0</td>
      <td>80.0</td>
      <td>79.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>25097</th>
      <td>7.5</td>
      <td>21.3</td>
      <td>0.0</td>
      <td>4.7</td>
      <td>8.4</td>
      <td>15.0</td>
      <td>2.0</td>
      <td>7.0</td>
      <td>88.0</td>
      <td>52.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 118 columns</p>
</div>


이제 훈련셋과 데이터셋을 만들었으니 각 특성들에 대해 스케일링을 합니다.


# **11. Feature Scaling** <a class="anchor" id="11"></a>





[Table of Contents](#0.1)



```python
X_train.describe()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>...</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>...</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>12.190189</td>
      <td>23.203107</td>
      <td>0.670800</td>
      <td>5.093362</td>
      <td>7.982476</td>
      <td>39.982091</td>
      <td>14.029381</td>
      <td>18.687466</td>
      <td>68.950691</td>
      <td>51.605828</td>
      <td>...</td>
      <td>0.054078</td>
      <td>0.059123</td>
      <td>0.068447</td>
      <td>0.103723</td>
      <td>0.065224</td>
      <td>0.056055</td>
      <td>0.064786</td>
      <td>0.069323</td>
      <td>0.060309</td>
      <td>0.064958</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6.366893</td>
      <td>7.085408</td>
      <td>1.181512</td>
      <td>2.800200</td>
      <td>2.761639</td>
      <td>13.127953</td>
      <td>8.835596</td>
      <td>8.700618</td>
      <td>18.811437</td>
      <td>20.439999</td>
      <td>...</td>
      <td>0.226173</td>
      <td>0.235855</td>
      <td>0.252512</td>
      <td>0.304902</td>
      <td>0.246922</td>
      <td>0.230029</td>
      <td>0.246149</td>
      <td>0.254004</td>
      <td>0.238059</td>
      <td>0.246452</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-8.500000</td>
      <td>-4.800000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>6.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.700000</td>
      <td>18.000000</td>
      <td>0.000000</td>
      <td>4.000000</td>
      <td>8.200000</td>
      <td>31.000000</td>
      <td>7.000000</td>
      <td>13.000000</td>
      <td>57.000000</td>
      <td>37.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>12.000000</td>
      <td>22.600000</td>
      <td>0.000000</td>
      <td>4.700000</td>
      <td>8.400000</td>
      <td>39.000000</td>
      <td>13.000000</td>
      <td>19.000000</td>
      <td>70.000000</td>
      <td>52.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>16.800000</td>
      <td>28.200000</td>
      <td>0.600000</td>
      <td>5.200000</td>
      <td>8.600000</td>
      <td>46.000000</td>
      <td>19.000000</td>
      <td>24.000000</td>
      <td>83.000000</td>
      <td>65.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>31.900000</td>
      <td>48.100000</td>
      <td>3.200000</td>
      <td>21.800000</td>
      <td>14.500000</td>
      <td>135.000000</td>
      <td>55.000000</td>
      <td>57.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>...</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 118 columns</p>
</div>



```python
cols = X_train.columns
```


```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

X_train = scaler.fit_transform(X_train)

X_test = scaler.transform(X_test)
```


```python
X_train = pd.DataFrame(X_train, columns=[cols])
```


```python
X_test = pd.DataFrame(X_test, columns=[cols])
```


```python
X_train.describe()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th>MinTemp</th>
      <th>MaxTemp</th>
      <th>Rainfall</th>
      <th>Evaporation</th>
      <th>Sunshine</th>
      <th>WindGustSpeed</th>
      <th>WindSpeed9am</th>
      <th>WindSpeed3pm</th>
      <th>Humidity9am</th>
      <th>Humidity3pm</th>
      <th>...</th>
      <th>NNW</th>
      <th>NW</th>
      <th>S</th>
      <th>SE</th>
      <th>SSE</th>
      <th>SSW</th>
      <th>SW</th>
      <th>W</th>
      <th>WNW</th>
      <th>WSW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>...</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
      <td>116368.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.512133</td>
      <td>0.529359</td>
      <td>0.209625</td>
      <td>0.233640</td>
      <td>0.550516</td>
      <td>0.263427</td>
      <td>0.255080</td>
      <td>0.327850</td>
      <td>0.689507</td>
      <td>0.516058</td>
      <td>...</td>
      <td>0.054078</td>
      <td>0.059123</td>
      <td>0.068447</td>
      <td>0.103723</td>
      <td>0.065224</td>
      <td>0.056055</td>
      <td>0.064786</td>
      <td>0.069323</td>
      <td>0.060309</td>
      <td>0.064958</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.157596</td>
      <td>0.133940</td>
      <td>0.369223</td>
      <td>0.128450</td>
      <td>0.190458</td>
      <td>0.101767</td>
      <td>0.160647</td>
      <td>0.152642</td>
      <td>0.188114</td>
      <td>0.204400</td>
      <td>...</td>
      <td>0.226173</td>
      <td>0.235855</td>
      <td>0.252512</td>
      <td>0.304902</td>
      <td>0.246922</td>
      <td>0.230029</td>
      <td>0.246149</td>
      <td>0.254004</td>
      <td>0.238059</td>
      <td>0.246452</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.400990</td>
      <td>0.431002</td>
      <td>0.000000</td>
      <td>0.183486</td>
      <td>0.565517</td>
      <td>0.193798</td>
      <td>0.127273</td>
      <td>0.228070</td>
      <td>0.570000</td>
      <td>0.370000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.507426</td>
      <td>0.517958</td>
      <td>0.000000</td>
      <td>0.215596</td>
      <td>0.579310</td>
      <td>0.255814</td>
      <td>0.236364</td>
      <td>0.333333</td>
      <td>0.700000</td>
      <td>0.520000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.626238</td>
      <td>0.623819</td>
      <td>0.187500</td>
      <td>0.238532</td>
      <td>0.593103</td>
      <td>0.310078</td>
      <td>0.345455</td>
      <td>0.421053</td>
      <td>0.830000</td>
      <td>0.650000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>...</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 118 columns</p>
</div>


여전히 테스트셋은 훈련을 시키지 않도록 주의해야합니다.

이제 훈련을 시작해봅시다.




## (수정됨)이후 코드를 진행하기 전 y데이터셋에도 결측값이 있는 것을 확인 아래코드를 추가하여 결측치를 처리합니다.



```python
from sklearn.preprocessing import LabelEncoder

y_train = pd.DataFrame(y_train)
y_test = pd.DataFrame(y_test)

y_train['RainTomorrow'].fillna(y_train['RainTomorrow'].mode()[0], inplace=True)
y_test['RainTomorrow'].fillna(y_test['RainTomorrow'].mode()[0], inplace=True)

train_le = LabelEncoder()
test_le = LabelEncoder()

train_le.fit(y_train['RainTomorrow'].astype('str').drop_duplicates())
test_le.fit(y_test['RainTomorrow'].astype('str').drop_duplicates())

y_train['enc'] = train_le.transform(y_train['RainTomorrow'].astype('str'))
y_test['enc_test'] = test_le.transform(y_test['RainTomorrow'].astype('str'))

y_train.drop(columns=['RainTomorrow'], inplace=True)
y_test.drop(columns=['RainTomorrow'], inplace=True)
```

# **12. Model training** <a class="anchor" id="12"></a>





[Table of Contents](#0.1)



```python
# train a logistic regression model on the training set
from sklearn.linear_model import LogisticRegression


# instantiate the model
logreg = LogisticRegression(solver='liblinear', random_state=0)


# fit the model
logreg.fit(X_train, y_train)
```

<pre>
LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
                   intercept_scaling=1, l1_ratio=None, max_iter=100,
                   multi_class='warn', n_jobs=None, penalty='l2',
                   random_state=0, solver='liblinear', tol=0.0001, verbose=0,
                   warm_start=False)
</pre>
# **13. Predict results** <a class="anchor" id="13"></a>





[Table of Contents](#0.1)



```python
y_pred_test = logreg.predict(X_test)

y_pred_test
```

<pre>
array([0, 0, 0, ..., 1, 0, 0])
</pre>
### predict_proba method





predict_proba() 메서드는 이 경우와 같이 이진 분류 문제에서 대상 변수(0과 1)에 대한 확률을 배열 형태로 반환합니다. 여기서 0은 비가 오지 않을 확률, 1은 비가 올 확률입니다. 예측된 확률이 0.4이면, 해당 데이터에 대해 모델은 비가 오지 않을 확률이 0.6, 비가 올 확률이 0.4라고 예측한 것입니다.



```python
# probability of getting output as 0 - no rain

logreg.predict_proba(X_test)[:,0]
```

<pre>
array([0.83218012, 0.74547897, 0.79864899, ..., 0.42025828, 0.65746991,
       0.96954653])
</pre>

```python
# probability of getting output as 1 - rain

logreg.predict_proba(X_test)[:,1]
```

<pre>
array([0.16781988, 0.25452103, 0.20135101, ..., 0.57974172, 0.34253009,
       0.03045347])
</pre>
# **14. Check accuracy score** <a class="anchor" id="14"></a>





[Table of Contents](#0.1)



```python
from sklearn.metrics import accuracy_score

print('Model accuracy score: {0:0.4f}'. format(accuracy_score(y_test, y_pred_test)))
```

<pre>
Model accuracy score: 0.8484
</pre>
y_test가 테스트 세트에서의 실제 클래스 레이블을 나타내며, y_pred_test는 모델이 테스트 세트에 대해 예측한 클래스 레이블을 나타냅니다. 이 두 값은 모델이 얼마나 정확하게 분류를 수행했는지를 평가하기 위해 비교되고, 이를 통해 모델의 성능을 평가할 수 있습니다.


### Compare the train-set and test-set accuracy





이제 과적합을 확인하기 위해 학습 세트와 테스트 세트 정확도를 비교해보겠습니다.



```python
y_pred_train = logreg.predict(X_train)

y_pred_train
```

<pre>
array([0, 0, 0, ..., 0, 0, 0])
</pre>

```python
print('Training-set accuracy score: {0:0.4f}'. format(accuracy_score(y_train, y_pred_train)))
```

<pre>
Training-set accuracy score: 0.8488
</pre>
### Check for overfitting and underfitting



```python
# print the scores on training and test set

print('Training set score: {:.4f}'.format(logreg.score(X_train, y_train)))

print('Test set score: {:.4f}'.format(logreg.score(X_test, y_test)))
```

<pre>
Training set score: 0.8488
Test set score: 0.8484
</pre>
훈련 세트의 정확도 점수는 0.8488이고 테스트 세트의 정확도는 0.8484입니다. 이 두 값은 매우 비슷합니다. 따라서 과적합 문제는 없습니다.



로지스틱 회귀에서 C 값의 기본값은 1입니다. 이 값은 훈련 세트와 테스트 세트 모두 약 85%의 정확도로 좋은 성능을 제공합니다. 그러나 훈련 세트와 테스트 세트 모두에서 모델의 성능이 매우 유사하다는 것은 과소적합의 가능성이 높습니다.



따라서 C 값을 증가시켜 더 유연한 모델을 적합시키려고 합니다.



```python
# fit the Logsitic Regression model with C=100

# instantiate the model
logreg100 = LogisticRegression(C=100, solver='liblinear', random_state=0)


# fit the model
logreg100.fit(X_train, y_train)
```

<pre>
LogisticRegression(C=100, class_weight=None, dual=False, fit_intercept=True,
                   intercept_scaling=1, l1_ratio=None, max_iter=100,
                   multi_class='warn', n_jobs=None, penalty='l2',
                   random_state=0, solver='liblinear', tol=0.0001, verbose=0,
                   warm_start=False)
</pre>

```python
# print the scores on training and test set

print('Training set score: {:.4f}'.format(logreg100.score(X_train, y_train)))

print('Test set score: {:.4f}'.format(logreg100.score(X_test, y_test)))
```

<pre>
Training set score: 0.8489
Test set score: 0.8491
</pre>
이전 모델에서 C=1 값을 사용했을 때 학습 데이터와 테스트 데이터 모두 약 85%의 정확도를 보였습니다. 그러나 이 두 값이 매우 유사하다는 것은 과소적합(underfitting)의 가능성이 있다는 것을 의미합니다. 따라서 C 값을 높여 더 복잡한 모델을 적합시키고, 성능을 비교해보았습니다. C=100일 때 테스트 데이터 정확도가 더 높게 나오는 것을 확인할 수 있으며, 약간의 학습 데이터 정확도 상승도 보입니다. 이를 통해 더 복잡한 모델이 더 좋은 성능을 보일 것으로 결론지었습니다.


이제 C=1 기본값보다 더 규제된 모델을 사용하여 조사해 보겠습니다. C를 0.01로 설정합니다.



```python
# fit the Logsitic Regression model with C=001

# instantiate the model
logreg001 = LogisticRegression(C=0.01, solver='liblinear', random_state=0)


# fit the model
logreg001.fit(X_train, y_train)
```

<pre>
LogisticRegression(C=0.01, class_weight=None, dual=False, fit_intercept=True,
                   intercept_scaling=1, l1_ratio=None, max_iter=100,
                   multi_class='warn', n_jobs=None, penalty='l2',
                   random_state=0, solver='liblinear', tol=0.0001, verbose=0,
                   warm_start=False)
</pre>

```python
# print the scores on training and test set

print('Training set score: {:.4f}'.format(logreg001.score(X_train, y_train)))

print('Test set score: {:.4f}'.format(logreg001.score(X_test, y_test)))
```

<pre>
Training set score: 0.8427
Test set score: 0.8418
</pre>
C 값을 0.01로 설정하여 더 규제된 모델을 사용하면, 기본 매개변수에 비해 훈련 및 테스트 세트 정확도가 모두 낮아집니다.


### Compare model accuracy with null accuracy





위에서 언급한 것처럼, 모델의 정확도는 0.8501입니다. 그러나, 위의 정확도만으로는 모델이 얼마나 좋은지를 평가할 수 없습니다. 우리는 널(null) 정확도와 비교해야 합니다. 널 정확도는 항상 가장 빈번한 클래스를 예측함으로써 달성할 수 있는 정확도입니다.



그러므로, 먼저 테스트 세트에서 클래스 분포를 확인해야 합니다.



```python
# check class distribution in test set

# y_test.value_counts()
```


```python
# check null accuracy score

null_accuracy = (22067/(22067+6372))

print('Null accuracy score: {0:0.4f}'. format(null_accuracy))
```

<pre>
Null accuracy score: 0.7759
</pre>
예측 모델의 정확도 점수가 0.8501이고, Null 정확도 점수는 0.7759입니다. 따라서 우리는 로지스틱 회귀 모델이 클래스 레이블을 예측하는 데 아주 잘 수행되고 있다고 결론 짓을 수 있습니다.


위의 분석을 기반으로 우리는 분류 모델의 정확도가 매우 높다는 결론을 내릴 수 있습니다. 모델은 클래스 레이블을 예측하는 데 매우 잘하고 있습니다.



그러나 이는 값의 분포에 대한 정보를 제공하지 않으며, 분류기가 만드는 오류 유형에 대한 정보도 제공하지 않습니다.



이를 해결하기 위해 우리에게는 Confusion Matrix라는 도구가 있습니다.


# **15. Confusion matrix** <a class="anchor" id="15"></a>





[Table of Contents](#0.1)





분류 모델 성능을 평가하는 경우 네 가지 결과가 가능합니다. 이 네 가지 결과는 아래와 같이 설명됩니다.



True Positives (TP) - True Positives는 관측치가 특정 클래스에 속할 것으로 예측하고, 관측치가 실제로 그 클래스에 속한 경우입니다.



True Negatives (TN) - True Negatives는 관측치가 특정 클래스에 속하지 않을 것으로 예측하고, 관측치가 실제로 그 클래스에 속하지 않는 경우입니다.



False Positives (FP) - False Positives는 관측치가 특정 클래스에 속할 것으로 예측하지만, 관측치가 실제로 그 클래스에 속하지 않은 경우입니다. 이러한 유형의 오류를 Type I 오류라고 합니다.



False Negatives (FN) - False Negatives는 관측치가 특정 클래스에 속하지 않을 것으로 예측하지만, 관측치가 실제로 그 클래스에 속하는 경우입니다. 이는 매우 심각한 오류이며 Type II 오류라고 합니다.




```python
# Print the Confusion Matrix and slice it into four pieces

from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred_test)

print('Confusion matrix\n\n', cm)

print('\nTrue Positives(TP) = ', cm[0,0])

print('\nTrue Negatives(TN) = ', cm[1,1])

print('\nFalse Positives(FP) = ', cm[0,1])

print('\nFalse Negatives(FN) = ', cm[1,0])
```

<pre>
Confusion matrix

 [[21543  1183]
 [ 3227  3139]]

True Positives(TP) =  21543

True Negatives(TN) =  3139

False Positives(FP) =  1183

False Negatives(FN) =  3227
</pre>
이 행렬에서 `20892 + 3285 = 24177 correct predictions` 와 `3087 + 1175 = 4262 incorrect predictions`임을 알 수 있습니다..







- `True Positives` (Actual Positive:1 and Predict Positive:1) - 20892





- `True Negatives` (Actual Negative:0 and Predict Negative:0) - 3285





- `False Positives` (Actual Negative:0 but Predict Positive:1) - 1175 `(Type I error)`





- `False Negatives` (Actual Positive:1 but Predict Negative:0) - 3087 `(Type II error)`



```python
# visualize confusion matrix with seaborn heatmap

cm_matrix = pd.DataFrame(data=cm, columns=['Actual Positive:1', 'Actual Negative:0'], 
                                 index=['Predict Positive:1', 'Predict Negative:0'])

sns.heatmap(cm_matrix, annot=True, fmt='d', cmap='YlGnBu')
```

<pre>
<matplotlib.axes._subplots.AxesSubplot at 0x7db57d8ee940>
</pre>
<img src="data:image/png;base64,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"/>

# **16. Classification metrices** <a class="anchor" id="16"></a>





[Table of Contents](#0.1)


## Classification Report





분류 보고서(Classification report)는 분류 모델의 성능을 평가하는 또 다른 방법입니다. 모델의 정밀도, 재현율, f1-score 및 지원도 점수를 표시합니다.



```python
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred_test))
```

<pre>
              precision    recall  f1-score   support

           0       0.87      0.95      0.91     22726
           1       0.73      0.49      0.59      6366

    accuracy                           0.85     29092
   macro avg       0.80      0.72      0.75     29092
weighted avg       0.84      0.85      0.84     29092

</pre>
## Classification accuracy



```python
TP = cm[0,0]
TN = cm[1,1]
FP = cm[0,1]
FN = cm[1,0]
```


```python
# print classification accuracy

classification_accuracy = (TP + TN) / float(TP + TN + FP + FN)

print('Classification accuracy : {0:0.4f}'.format(classification_accuracy))
```

<pre>
Classification accuracy : 0.8484
</pre>
## Classification error



```python
# print classification error

classification_error = (FP + FN) / float(TP + TN + FP + FN)

print('Classification error : {0:0.4f}'.format(classification_error))
```

<pre>
Classification error : 0.1516
</pre>
## Precision





**정밀도(Precision)**는 예측한 양성 클래스 샘플 중 실제 양성 클래스 샘플의 비율입니다. 즉, 참 양성(TP) 샘플 수를 예측한 양성(TP + FP) 샘플 수로 나눈 값입니다.



따라서 정밀도는 양성 클래스보다는 음성 클래스보다 더 관심이 있는 결과입니다.



수학적으로는 정밀도는 TP / (TP + FP)의 비율로 정의됩니다.








```python
# print precision score

precision = TP / float(TP + FP)


print('Precision : {0:0.4f}'.format(precision))
```

<pre>
Precision : 0.9479
</pre>
## Recall





**재현율(Recall)**은 실제 양성 클래스에 속한 샘플 중에서 정확하게 예측된 샘플의 비율을 뜻합니다.



즉, TP(True Positive)의 비율로 정의할 수 있으며, 진짜 양성(TP)과 거짓 음성(FN)의 합인 (TP + FN)으로 나눈 값입니다.



민감도(Sensitivity)라고도 불립니다.










```python
recall = TP / float(TP + FN)

print('Recall or Sensitivity : {0:0.4f}'.format(recall))
```

<pre>
Recall or Sensitivity : 0.8697
</pre>
## True Positive Rate





**True Positive Rate** is synonymous with **Recall**.




```python
true_positive_rate = TP / float(TP + FN)


print('True Positive Rate : {0:0.4f}'.format(true_positive_rate))
```

<pre>
True Positive Rate : 0.8697
</pre>
## False Positive Rate



```python
false_positive_rate = FP / float(FP + TN)


print('False Positive Rate : {0:0.4f}'.format(false_positive_rate))
```

<pre>
False Positive Rate : 0.2737
</pre>
## Specificity



```python
specificity = TN / (TN + FP)

print('Specificity : {0:0.4f}'.format(specificity))
```

<pre>
Specificity : 0.7263
</pre>
## f1-score





f1-score는 정밀도와 재현율의 가중 조화 평균입니다. 최적의 f1-score는 1.0이고, 최악은 0.0입니다. f1-score는 정밀도와 재현율의 조화 평균이므로, 정확도 측정값보다 항상 낮습니다. 가중치 평균 f1-score를 사용하여 분류 모델을 비교해야 하며, 전체적인 정확도 측정값보다 유용합니다.





## Support





Support는 데이터셋에서 해당 클래스가 실제로 발생한 횟수를 의미합니다.


# **17. Adjusting the threshold level** <a class="anchor" id="17"></a>





[Table of Contents](#0.1)



```python
# print the first 10 predicted probabilities of two classes- 0 and 1

y_pred_prob = logreg.predict_proba(X_test)[0:10]

y_pred_prob
```

<pre>
array([[0.83218012, 0.16781988],
       [0.74547897, 0.25452103],
       [0.79864899, 0.20135101],
       [0.58509213, 0.41490787],
       [0.92165784, 0.07834216],
       [0.95625879, 0.04374121],
       [0.57881888, 0.42118112],
       [0.50293916, 0.49706084],
       [0.80281943, 0.19718057],
       [0.72340946, 0.27659054]])
</pre>
### Observations





- 각 행마다의 숫자들은 1로 합쳐집니다.

- 2개의 열은 0과 1의 2개의 클래스를 나타냅니다.



    - 클래스 0 - 내일 비가 오지 않을 확률에 대한 예측 확률입니다.



    - 클래스 1 - 내일 비가 올 확률에 대한 예측 확률입니다.



- 예측된 확률의 중요성



    - 우리는 비가 올 확률이나 오지 않을 확률에 따라 데이터를 순위대로 나열할 수 있습니다.



- predict_proba 과정



    - 확률을 예측합니다.



    - 가장 높은 확률의 클래스를 선택합니다.



- 분류 임계값



    - 분류 임계값은 0.5입니다.



    - 클래스 1 - 확률이 0.5보다 크면 비가 올 확률로 예측됩니다.



    - 클래스 0 - 확률이 0.5보다 작으면 비가 오지 않을 확률로 예측됩니다.  

    




```python
# store the probabilities in dataframe

y_pred_prob_df = pd.DataFrame(data=y_pred_prob, columns=['Prob of - No rain tomorrow (0)', 'Prob of - Rain tomorrow (1)'])

y_pred_prob_df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prob of - No rain tomorrow (0)</th>
      <th>Prob of - Rain tomorrow (1)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.832180</td>
      <td>0.167820</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.745479</td>
      <td>0.254521</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.798649</td>
      <td>0.201351</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.585092</td>
      <td>0.414908</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.921658</td>
      <td>0.078342</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.956259</td>
      <td>0.043741</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.578819</td>
      <td>0.421181</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0.502939</td>
      <td>0.497061</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0.802819</td>
      <td>0.197181</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0.723409</td>
      <td>0.276591</td>
    </tr>
  </tbody>
</table>
</div>



```python
# print the first 10 predicted probabilities for class 1 - Probability of rain

logreg.predict_proba(X_test)[0:10, 1]
```

<pre>
array([0.16781988, 0.25452103, 0.20135101, 0.41490787, 0.07834216,
       0.04374121, 0.42118112, 0.49706084, 0.19718057, 0.27659054])
</pre>

```python
# store the predicted probabilities for class 1 - Probability of rain

y_pred1 = logreg.predict_proba(X_test)[:, 1]
```


```python
# plot histogram of predicted probabilities


# adjust the font size 
plt.rcParams['font.size'] = 12


# plot histogram with 10 bins
plt.hist(y_pred1, bins = 10)


# set the title of predicted probabilities
plt.title('Histogram of predicted probabilities of rain')


# set the x-axis limit
plt.xlim(0,1)


# set the title
plt.xlabel('Predicted probabilities of rain')
plt.ylabel('Frequency')
```

<pre>
Text(0, 0.5, 'Frequency')
</pre>
<img src="data:image/png;base64,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"/>

### Observations





- 위의 히스토그램은 매우 양의 왜도(skewed)를 가진 것으로 나타납니다.

- 첫 번째 열은 약 0.0에서 0.1 사이의 확률을 가진 약 15,000개의 관측치가 있음을 알려줍니다.

- 확률이 0.5보다 큰 작은 수의 관측치가 있습니다.

- 따라서 이 작은 수의 관측치는 내일 비가 올 것이라고 예측합니다.

- 대다수의 관측치는 내일 비가 오지 않을 것으로 예측합니다.


### Lower the threshold


아래 코드는 이론상 옳지만 필자도 알 수 없는 이유로 오류가 발생하여 주석 처리합니다.



예측컨데 y_test에서 오류가 발생했을 것이지만 과정이 너무 복잡할 것 같아서 이후에 처리하도록 합니다.



```python
# from sklearn.preprocessing import LabelEncoder

# # LabelEncoder를 사용하여 y_train과 y_test 레이블을 숫자형으로 변환
# le = LabelEncoder()
# y_train = le.fit_transform(y_train['enc'])
# y_test = le.transform(y_test['enc'])

# for i in range(1,5):
    
#     cm1=0
    
#     y_pred1 = logreg.predict_proba(X_test)[:,1]
    
#     y_pred1 = y_pred1.reshape(-1,1)
    
#     y_pred2 = binarize(y_pred1, i/10)
    
#     y_pred2 = np.where(y_pred2 == 1, 'Yes', 'No')
    
#     cm1 = confusion_matrix(y_test, y_pred2)
        
#     print ('With',i/10,'threshold the Confusion Matrix is ','\n\n',cm1,'\n\n',
           
#             'with',cm1[0,0]+cm1[1,1],'correct predictions, ', '\n\n', 
           
#             cm1[0,1],'Type I errors( False Positives), ','\n\n',
           
#             cm1[1,0],'Type II errors( False Negatives), ','\n\n',
           
#            'Accuracy score: ', (accuracy_score(y_test, y_pred2)), '\n\n',
           
#            'Sensitivity: ',cm1[1,1]/(float(cm1[1,1]+cm1[1,0])), '\n\n',
           
#            'Specificity: ',cm1[0,0]/(float(cm1[0,0]+cm1[0,1])),'\n\n',
          
#             '====================================================', '\n\n')
```

### Comments





- 이진 분류 문제에서는, 예측된 확률을 클래스 예측으로 변환하기 위해 기본적으로 0.5의 임계값이 사용됩니다.

- 임계값은 민감도 또는 특이도를 높이기 위해 조정될 수 있습니다.

- 민감도와 특이도는 서로 역관계를 가집니다. 한 쪽을 높이면 다른 쪽은 반드시 낮아집니다.

- 임계값을 높이면 정확도가 증가하는 것을 확인할 수 있습니다.

- 임계값을 조정하는 것은 모델 구축 과정에서 마지막 단계 중 하나여야 합니다.


# **18. ROC - AUC** <a class="anchor" id="18"></a>





[Table of Contents](#0.1)







## ROC Curve





분류 모델의 성능을 시각적으로 측정하는 또 다른 도구는 ROC Curve입니다. ROC Curve는 Receiver Operating Characteristic Curve의 약자로, 다양한 분류 임계값에서 분류 모델의 성능을 보여주는 그래프입니다.



ROC Curve는 다양한 임계값에서 **True Positive Rate (TPR)**와 **False Positive Rate (FPR)**를 플롯합니다.



**True Positive Rate (TPR)**는 Recall이라고도하며, TP / (TP + FN)의 비율로 정의됩니다.



**False Positive Rate (FPR)**는 FP / (FP + TN)의 비율로 정의됩니다.



ROC Curve에서는 하나의 지점의 TPR (True Positive Rate)과 FPR (False Positive Rate)에 초점을 맞춥니다. 이는 다양한 임계값에서 TPR과 FPR로 구성된 ROC Curve의 일반적인 성능을 제공합니다. 따라서 ROC Curve는 다른 분류 임계값에서 TPR 대 FPR을 플롯합니다. 임계값을 낮추면 더 많은 항목이 긍정으로 분류될 수 있습니다. 이는 True Positive (TP)와 False Positive (FP) 모두를 증가시킵니다.





위와 같은 이유로 y_test에 문제가 생겨 곡선이 그려지지 않으므로 이또한 주석처리하고 개념만 정리합니다.



```python
# # plot ROC Curve

# from sklearn.metrics import roc_curve

# fpr, tpr, thresholds = roc_curve(y_test, y_pred1, pos_label = 'Yes')

# plt.figure(figsize=(6,4))

# plt.plot(fpr, tpr, linewidth=2)

# plt.plot([0,1], [0,1], 'k--' )

# plt.rcParams['font.size'] = 12

# plt.title('ROC curve for RainTomorrow classifier')

# plt.xlabel('False Positive Rate (1 - Specificity)')

# plt.ylabel('True Positive Rate (Sensitivity)')

# plt.show()
```

ROC 곡선은 특정 맥락에서 민감도와 특이도를 균형있게 조절하는 임계값을 선택하는 데 도움을 줍니다.


## ROC-AUC





**ROC AUC**는 Receiver Operating Characteristic - Area Under Curve의 약어로, 분류 모델의 성능을 비교하는 기술입니다. 이 기술에서는 곡선 아래 면적 (AUC)을 측정합니다. 완벽한 분류 모델은 ROC AUC가 1이 되고, 완전한 랜덤 분류 모델은 ROC AUC가 0.5가 됩니다.



따라서 ROC AUC는 ROC 그래프에서 곡선 아래에 있는 영역의 백분율입니다.



```python
# compute ROC AUC

from sklearn.metrics import roc_auc_score

ROC_AUC = roc_auc_score(y_test, y_pred1)

print('ROC AUC : {:.4f}'.format(ROC_AUC))
```

<pre>
ROC AUC : 0.8671
</pre>
### Comments





- ROC AUC는 분류기의 성능을 나타내는 단일 숫자 요약값입니다. 값이 높을수록 분류기의 성능이 좋습니다.



- 우리 모델의 ROC AUC 값이 1에 가까워지므로, 우리의 분류기가 내일 비가 올지 여부를 예측하는 데에 잘 작동한다는 결론을 내릴 수 있습니다.



```python
# calculate cross-validated ROC AUC 

from sklearn.model_selection import cross_val_score

Cross_validated_ROC_AUC = cross_val_score(logreg, X_train, y_train, cv=5, scoring='roc_auc').mean()

print('Cross validated ROC AUC : {:.4f}'.format(Cross_validated_ROC_AUC))
```

<pre>
Cross validated ROC AUC : 0.8675
</pre>
# **19. k-Fold Cross Validation** <a class="anchor" id="19"></a>





[Table of Contents](#0.1)



```python
# Applying 5-Fold Cross Validation

from sklearn.model_selection import cross_val_score

scores = cross_val_score(logreg, X_train, y_train, cv = 5, scoring='accuracy')

print('Cross-validation scores:{}'.format(scores))
```

<pre>
Cross-validation scores:[0.84803437 0.8493598  0.8493963  0.84501353 0.84879474]
</pre>
교차 검증 정확도를 요약하기 위해 평균을 계산할 수 있습니다.



```python
# compute Average cross-validation score

print('Average cross-validation score: {:.4f}'.format(scores.mean()))
```

<pre>
Average cross-validation score: 0.8481
</pre>
우리의 원래 모델 점수는 0.8476입니다. 평균 교차 검증 점수는 0.8474입니다. 따라서 교차 검증은 성능 향상을 가져오지 않는다고 결론 짓을 수 있습니다.


# **20. Hyperparameter Optimization using GridSearch CV** <a class="anchor" id="20"></a>





[Table of Contents](#0.1)



```python
from sklearn.model_selection import GridSearchCV


parameters = [{'penalty':['l1','l2']}, 
              {'C':[1, 10, 100, 1000]}]



grid_search = GridSearchCV(estimator = logreg,  
                           param_grid = parameters,
                           scoring = 'accuracy',
                           cv = 5,
                           verbose=0)


grid_search.fit(X_train, y_train)
```

<pre>
GridSearchCV(cv=5, error_score='raise-deprecating',
             estimator=LogisticRegression(C=1.0, class_weight=None, dual=False,
                                          fit_intercept=True,
                                          intercept_scaling=1, l1_ratio=None,
                                          max_iter=100, multi_class='warn',
                                          n_jobs=None, penalty='l2',
                                          random_state=0, solver='liblinear',
                                          tol=0.0001, verbose=0,
                                          warm_start=False),
             iid='warn', n_jobs=None,
             param_grid=[{'penalty': ['l1', 'l2']}, {'C': [1, 10, 100, 1000]}],
             pre_dispatch='2*n_jobs', refit=True, return_train_score=False,
             scoring='accuracy', verbose=0)
</pre>

```python
# examine the best model

# best score achieved during the GridSearchCV
print('GridSearch CV best score : {:.4f}\n\n'.format(grid_search.best_score_))

# print parameters that give the best results
print('Parameters that give the best results :','\n\n', (grid_search.best_params_))

# print estimator that was chosen by the GridSearch
print('\n\nEstimator that was chosen by the search :','\n\n', (grid_search.best_estimator_))
```

<pre>
GridSearch CV best score : 0.8483


Parameters that give the best results : 

 {'penalty': 'l1'}


Estimator that was chosen by the search : 

 LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
                   intercept_scaling=1, l1_ratio=None, max_iter=100,
                   multi_class='warn', n_jobs=None, penalty='l1',
                   random_state=0, solver='liblinear', tol=0.0001, verbose=0,
                   warm_start=False)
</pre>

```python
# calculate GridSearch CV score on test set

print('GridSearch CV score on test set: {0:0.4f}'.format(grid_search.score(X_test, y_test)))
```

<pre>
GridSearch CV score on test set: 0.8488
</pre>
### Comments





원래 모델의 테스트 정확도는 0.8483이고, GridSearch CV 정확도는 0.8488입니다. 이를 통해 우리는 GridSearch CV가 이 모델에서 성능을 개선시켰음을 알 수 있습니다.


# **21. Results and conclusion** <a class="anchor" id="21"></a>





[Table of Contents](#0.1)


1. 로지스틱 회귀 모델의 정확도 점수는 0.8483입니다. 따라서 모델은 오늘 오스트레일리아에서 비가 올 것인지 아닌지 예측하는 데 매우 잘 작동합니다.



2. 적은 수의 관측치들이 내일 비가 올 것이라고 예측하고, 대부분의 관측치들은 내일 비가 오지 않을 것이라고 예측합니다.



3. 모델은 과적합의 징후가 없습니다.



4. C 값의 증가는 테스트 집합의 정확도와 약간 증가된 학습 집합의 정확도를 초래합니다. 따라서 더 복잡한 모델이 더 나은 성능을 발휘할 것으로 결론 짓을 수 있습니다.



5. 임계값을 높이면 정확도가 높아집니다.



6. 모델의 ROC AUC는 1에 가까워지므로, 모델은 내일 비가 올지 여부를 예측하는 데 우수한 성능을 발휘한다는 결론을 내릴 수 있습니다.



7. 원래 모델의 정확도 점수는 0.8483이고, RFECV 후 정확도 점수는 0.8488입니다. 따라서 거의 동일한 정확도를 얻지만 feature의 수는 줄어듭니다.



8. 원래 모델에서 FP = 1175이고, FP1 = 1174입니다. 따라서 거짓 양성의 수가 거의 동일합니다. 또한 FN = 3087이고, FN1 = 3091입니다. 따라서 거짓 음성의 수가 약간 더 높습니다.



9. 원래 모델 점수는 0.8476입니다. 평균 교차 검증 점수는 0.8474입니다. 따라서 교차 검증은 성능 향상을 가져오지 않는 것으로 결론짓을 수 있습니다.



10. 원래 모델의 테스트 정확도는 0.8501이고, GridSearch CV의 정확도는 0.8507입니다. 이 모델에 대해 GridSearch CV가 성능을 향상시켰음을 알 수 있습니다.



# **22. References** <a class="anchor" id="22"></a>





[Table of Contents](#0.1)







The work done in this project is inspired from following books and websites:-





1. Hands on Machine Learning with Scikit-Learn and Tensorflow by Aurélién Géron



2. Introduction to Machine Learning with Python by Andreas C. Müller and Sarah Guido



3. Udemy course – Machine Learning – A Z by Kirill Eremenko and Hadelin de Ponteves



4. Udemy course – Feature Engineering for Machine Learning by Soledad Galli



5. Udemy course – Feature Selection for Machine Learning by Soledad Galli



6. https://en.wikipedia.org/wiki/Logistic_regression



7. https://ml-cheatsheet.readthedocs.io/en/latest/logistic_regression.html



8. https://en.wikipedia.org/wiki/Sigmoid_function



9. https://www.statisticssolutions.com/assumptions-of-logistic-regression/



10. https://www.kaggle.com/mnassrib/titanic-logistic-regression-with-python



11. https://www.kaggle.com/neisha/heart-disease-prediction-using-logistic-regression



12. https://www.ritchieng.com/machine-learning-evaluate-classification-model/



[Go to Top](#0)

