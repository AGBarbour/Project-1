

```python
import csv
import os
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
file = os.path.join('data', 'Batting.csv')
batters = pd.read_csv(file)
batters.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>stint</th>
      <th>teamID</th>
      <th>lgID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>...</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>abercda01</td>
      <td>1871</td>
      <td>1</td>
      <td>TRO</td>
      <td>NaN</td>
      <td>1</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>addybo01</td>
      <td>1871</td>
      <td>1</td>
      <td>RC1</td>
      <td>NaN</td>
      <td>25</td>
      <td>118</td>
      <td>30</td>
      <td>32</td>
      <td>6</td>
      <td>...</td>
      <td>13.0</td>
      <td>8.0</td>
      <td>1.0</td>
      <td>4</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>allisar01</td>
      <td>1871</td>
      <td>1</td>
      <td>CL1</td>
      <td>NaN</td>
      <td>29</td>
      <td>137</td>
      <td>28</td>
      <td>40</td>
      <td>4</td>
      <td>...</td>
      <td>19.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>allisdo01</td>
      <td>1871</td>
      <td>1</td>
      <td>WS3</td>
      <td>NaN</td>
      <td>27</td>
      <td>133</td>
      <td>28</td>
      <td>44</td>
      <td>10</td>
      <td>...</td>
      <td>27.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ansonca01</td>
      <td>1871</td>
      <td>1</td>
      <td>RC1</td>
      <td>NaN</td>
      <td>25</td>
      <td>120</td>
      <td>29</td>
      <td>39</td>
      <td>11</td>
      <td>...</td>
      <td>16.0</td>
      <td>6.0</td>
      <td>2.0</td>
      <td>2</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
file = os.path.join('data', 'People.csv')
people = pd.read_csv(file)
people.head()
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
      <th>playerID</th>
      <th>birthYear</th>
      <th>birthMonth</th>
      <th>birthDay</th>
      <th>birthCountry</th>
      <th>birthState</th>
      <th>birthCity</th>
      <th>deathYear</th>
      <th>deathMonth</th>
      <th>deathDay</th>
      <th>...</th>
      <th>nameLast</th>
      <th>nameGiven</th>
      <th>weight</th>
      <th>height</th>
      <th>bats</th>
      <th>throws</th>
      <th>debut</th>
      <th>finalGame</th>
      <th>retroID</th>
      <th>bbrefID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>1981.0</td>
      <td>12.0</td>
      <td>27.0</td>
      <td>USA</td>
      <td>CO</td>
      <td>Denver</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Aardsma</td>
      <td>David Allan</td>
      <td>215.0</td>
      <td>75.0</td>
      <td>R</td>
      <td>R</td>
      <td>2004-04-06</td>
      <td>2015-08-23</td>
      <td>aardd001</td>
      <td>aardsda01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aaronha01</td>
      <td>1934.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>USA</td>
      <td>AL</td>
      <td>Mobile</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Aaron</td>
      <td>Henry Louis</td>
      <td>180.0</td>
      <td>72.0</td>
      <td>R</td>
      <td>R</td>
      <td>1954-04-13</td>
      <td>1976-10-03</td>
      <td>aaroh101</td>
      <td>aaronha01</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aaronto01</td>
      <td>1939.0</td>
      <td>8.0</td>
      <td>5.0</td>
      <td>USA</td>
      <td>AL</td>
      <td>Mobile</td>
      <td>1984.0</td>
      <td>8.0</td>
      <td>16.0</td>
      <td>...</td>
      <td>Aaron</td>
      <td>Tommie Lee</td>
      <td>190.0</td>
      <td>75.0</td>
      <td>R</td>
      <td>R</td>
      <td>1962-04-10</td>
      <td>1971-09-26</td>
      <td>aarot101</td>
      <td>aaronto01</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aasedo01</td>
      <td>1954.0</td>
      <td>9.0</td>
      <td>8.0</td>
      <td>USA</td>
      <td>CA</td>
      <td>Orange</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Aase</td>
      <td>Donald William</td>
      <td>190.0</td>
      <td>75.0</td>
      <td>R</td>
      <td>R</td>
      <td>1977-07-26</td>
      <td>1990-10-03</td>
      <td>aased001</td>
      <td>aasedo01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>abadan01</td>
      <td>1972.0</td>
      <td>8.0</td>
      <td>25.0</td>
      <td>USA</td>
      <td>FL</td>
      <td>Palm Beach</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>Abad</td>
      <td>Fausto Andres</td>
      <td>184.0</td>
      <td>73.0</td>
      <td>L</td>
      <td>L</td>
      <td>2001-09-10</td>
      <td>2006-04-13</td>
      <td>abada001</td>
      <td>abadan01</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 24 columns</p>
</div>




```python
people2 = people[['playerID', 'birthYear']]
people2.head()
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
      <th>playerID</th>
      <th>birthYear</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>1981.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aaronha01</td>
      <td>1934.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aaronto01</td>
      <td>1939.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aasedo01</td>
      <td>1954.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>abadan01</td>
      <td>1972.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
batters2 = batters[batters.yearID >= 1900]
batters2.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>stint</th>
      <th>teamID</th>
      <th>lgID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>...</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7915</th>
      <td>allenbo01</td>
      <td>1900</td>
      <td>1</td>
      <td>CIN</td>
      <td>NL</td>
      <td>5</td>
      <td>15</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
      <td>...</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7916</th>
      <td>baileha01</td>
      <td>1900</td>
      <td>1</td>
      <td>BSN</td>
      <td>NL</td>
      <td>4</td>
      <td>9</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>...</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7917</th>
      <td>barreji01</td>
      <td>1900</td>
      <td>1</td>
      <td>CIN</td>
      <td>NL</td>
      <td>137</td>
      <td>545</td>
      <td>114</td>
      <td>172</td>
      <td>11</td>
      <td>...</td>
      <td>42.0</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>72</td>
      <td>63.0</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7918</th>
      <td>barrysh01</td>
      <td>1900</td>
      <td>1</td>
      <td>BSN</td>
      <td>NL</td>
      <td>81</td>
      <td>254</td>
      <td>40</td>
      <td>66</td>
      <td>10</td>
      <td>...</td>
      <td>37.0</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>13</td>
      <td>16.0</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7919</th>
      <td>beaumgi01</td>
      <td>1900</td>
      <td>1</td>
      <td>PIT</td>
      <td>NL</td>
      <td>138</td>
      <td>567</td>
      <td>105</td>
      <td>158</td>
      <td>14</td>
      <td>...</td>
      <td>50.0</td>
      <td>27.0</td>
      <td>NaN</td>
      <td>40</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>21.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
combined = batters2.groupby(['playerID','yearID'], as_index=False).sum()
combined.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>stint</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>2004</td>
      <td>1</td>
      <td>11</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aardsda01</td>
      <td>2006</td>
      <td>1</td>
      <td>45</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aardsda01</td>
      <td>2007</td>
      <td>1</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aardsda01</td>
      <td>2008</td>
      <td>1</td>
      <td>47</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aardsda01</td>
      <td>2009</td>
      <td>1</td>
      <td>73</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
yearly = batters2.groupby(['yearID'], as_index=False).sum()
yearly.head()
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
      <th>yearID</th>
      <th>stint</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1900</td>
      <td>202</td>
      <td>10874</td>
      <td>39132</td>
      <td>5932</td>
      <td>10925</td>
      <td>1432</td>
      <td>607</td>
      <td>254</td>
      <td>4924.0</td>
      <td>1686.0</td>
      <td>0.0</td>
      <td>3034</td>
      <td>2681.0</td>
      <td>0.0</td>
      <td>513.0</td>
      <td>806.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1901</td>
      <td>454</td>
      <td>20872</td>
      <td>77105</td>
      <td>11073</td>
      <td>20957</td>
      <td>2931</td>
      <td>1238</td>
      <td>455</td>
      <td>9136.0</td>
      <td>2851.0</td>
      <td>0.0</td>
      <td>5465</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>830.0</td>
      <td>1672.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1902</td>
      <td>526</td>
      <td>20916</td>
      <td>76157</td>
      <td>9879</td>
      <td>20318</td>
      <td>2830</td>
      <td>983</td>
      <td>356</td>
      <td>8245.0</td>
      <td>2678.0</td>
      <td>0.0</td>
      <td>5435</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>712.0</td>
      <td>1832.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1903</td>
      <td>433</td>
      <td>21128</td>
      <td>75439</td>
      <td>9888</td>
      <td>19776</td>
      <td>3034</td>
      <td>1161</td>
      <td>335</td>
      <td>8144.0</td>
      <td>2735.0</td>
      <td>0.0</td>
      <td>5369</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>729.0</td>
      <td>2019.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1904</td>
      <td>458</td>
      <td>23564</td>
      <td>82488</td>
      <td>9302</td>
      <td>20363</td>
      <td>2851</td>
      <td>1154</td>
      <td>331</td>
      <td>7590.0</td>
      <td>2780.0</td>
      <td>0.0</td>
      <td>5580</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>777.0</td>
      <td>2219.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
yearly['S%'] = (yearly['H']-yearly['2B']-yearly['3B']-yearly['HR'])/yearly['AB']
yearly['2B%'] = yearly['2B']/yearly['AB']
yearly['3B%'] = yearly['3B']/yearly['AB']
yearly['HR%'] = yearly['HR']/yearly['AB']
yearly['BB%'] = yearly['BB']/(yearly['AB']+yearly['BB'])
yearly['K%'] = yearly['SO']/yearly['AB']
yearly['SB%'] = yearly['SB']/(yearly['SB']+yearly['CS'])
yearly.head()
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
      <th>yearID</th>
      <th>stint</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
      <th>S%</th>
      <th>2B%</th>
      <th>3B%</th>
      <th>HR%</th>
      <th>BB%</th>
      <th>K%</th>
      <th>SB%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1900</td>
      <td>202</td>
      <td>10874</td>
      <td>39132</td>
      <td>5932</td>
      <td>10925</td>
      <td>1432</td>
      <td>607</td>
      <td>254</td>
      <td>4924.0</td>
      <td>...</td>
      <td>806.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.220587</td>
      <td>0.036594</td>
      <td>0.015512</td>
      <td>0.006491</td>
      <td>0.071954</td>
      <td>0.068512</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1901</td>
      <td>454</td>
      <td>20872</td>
      <td>77105</td>
      <td>11073</td>
      <td>20957</td>
      <td>2931</td>
      <td>1238</td>
      <td>455</td>
      <td>9136.0</td>
      <td>...</td>
      <td>1672.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.211828</td>
      <td>0.038013</td>
      <td>0.016056</td>
      <td>0.005901</td>
      <td>0.066186</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1902</td>
      <td>526</td>
      <td>20916</td>
      <td>76157</td>
      <td>9879</td>
      <td>20318</td>
      <td>2830</td>
      <td>983</td>
      <td>356</td>
      <td>8245.0</td>
      <td>...</td>
      <td>1832.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.212049</td>
      <td>0.037160</td>
      <td>0.012908</td>
      <td>0.004675</td>
      <td>0.066612</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1903</td>
      <td>433</td>
      <td>21128</td>
      <td>75439</td>
      <td>9888</td>
      <td>19776</td>
      <td>3034</td>
      <td>1161</td>
      <td>335</td>
      <td>8144.0</td>
      <td>...</td>
      <td>2019.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.202097</td>
      <td>0.040218</td>
      <td>0.015390</td>
      <td>0.004441</td>
      <td>0.066441</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1904</td>
      <td>458</td>
      <td>23564</td>
      <td>82488</td>
      <td>9302</td>
      <td>20363</td>
      <td>2851</td>
      <td>1154</td>
      <td>331</td>
      <td>7590.0</td>
      <td>...</td>
      <td>2219.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.194295</td>
      <td>0.034563</td>
      <td>0.013990</td>
      <td>0.004013</td>
      <td>0.063360</td>
      <td>0.000000</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>




```python
yearly = yearly.set_index('yearID')
```


```python
yearly.loc[[1998],['HR%']].values[0][0]
```




    0.030302304985758394




```python
total = batters2.sum()
total['G']
```




    4977926




```python
total['S%'] = (total['H']-total['2B']-total['3B']-total['HR'])/total['AB']
total['2B%'] = total['2B']/total['AB']
total['3B%'] = total['3B']/total['AB']
total['HR%'] = total['HR']/total['AB']
total['BB%'] = total['BB']/(total['AB']+total['BB'])
total['K%'] = total['SO']/total['AB']
total['SB%'] = total['SB']/(total['SB']+total['CS'])
total
```




    playerID    allenbo01baileha01barreji01barrysh01beaumgi01b...
    yearID                                              190058292
    stint                                                  103761
    teamID      CINBSNCINBSNPITCINNY1PHINY1CHNCINCHNSLNSLNCHNN...
    lgID        NLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNL...
    G                                                     4977926
    AB                                                   13312337
    R                                                     1721342
    H                                                     3479414
    2B                                                     600945
    3B                                                     111106
    HR                                                     286507
    RBI                                                1.5926e+06
    SB                                                     249865
    CS                                                      97480
    BB                                                    1255915
    SO                                                1.91754e+06
    IBB                                                     74239
    HBP                                                     96027
    SH                                                     216828
    SF                                                      71563
    GIDP                                                   232468
    S%                                                   0.186358
    2B%                                                  0.045142
    3B%                                                0.00834609
    HR%                                                 0.0215219
    BB%                                                  0.086209
    K%                                                   0.144042
    SB%                                                  0.719357
    dtype: object




```python
total
```




    playerID    allenbo01baileha01barreji01barrysh01beaumgi01b...
    yearID                                              190058292
    stint                                                  103761
    teamID      CINBSNCINBSNPITCINNY1PHINY1CHNCINCHNSLNSLNCHNN...
    lgID        NLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNLNL...
    G                                                     4977926
    AB                                                   13312337
    R                                                     1721342
    H                                                     3479414
    2B                                                     600945
    3B                                                     111106
    HR                                                     286507
    RBI                                                1.5926e+06
    SB                                                     249865
    CS                                                      97480
    BB                                                    1255915
    SO                                                1.91754e+06
    IBB                                                     74239
    HBP                                                     96027
    SH                                                     216828
    SF                                                      71563
    GIDP                                                   232468
    S%                                                   0.186358
    2B%                                                  0.045142
    3B%                                                0.00834609
    HR%                                                 0.0215219
    BB%                                                  0.086209
    K%                                                   0.144042
    SB%                                                  0.719357
    dtype: object




```python
ABpG = total['AB']/total['G']
avgG = total['yearID']/total['G']
avgSB = total['SB%']
avgG
```




    38.180216419448584




```python
combined = combined.drop(columns=['stint'])
combined.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>2004</td>
      <td>11</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aardsda01</td>
      <td>2006</td>
      <td>45</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aardsda01</td>
      <td>2007</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aardsda01</td>
      <td>2008</td>
      <td>47</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aardsda01</td>
      <td>2009</td>
      <td>73</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged = combined.merge(people2, how='inner', on = 'playerID')
merged.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>SB</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
      <th>birthYear</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>2004</td>
      <td>11</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aardsda01</td>
      <td>2006</td>
      <td>45</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aardsda01</td>
      <td>2007</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aardsda01</td>
      <td>2008</td>
      <td>47</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aardsda01</td>
      <td>2009</td>
      <td>73</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged['Age'] = merged['yearID']-merged['birthYear']
merged.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>CS</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
      <th>birthYear</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>2004</td>
      <td>11</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aardsda01</td>
      <td>2006</td>
      <td>45</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aardsda01</td>
      <td>2007</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aardsda01</td>
      <td>2008</td>
      <td>47</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aardsda01</td>
      <td>2009</td>
      <td>73</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>28.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
merged['PA'] = merged['AB'] + merged['BB'] + merged['HBP'] + merged['SH'] + merged['SF']
merged.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
      <th>birthYear</th>
      <th>Age</th>
      <th>PA</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aardsda01</td>
      <td>2004</td>
      <td>11</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>23.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aardsda01</td>
      <td>2006</td>
      <td>45</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>25.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>aardsda01</td>
      <td>2007</td>
      <td>25</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>26.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aardsda01</td>
      <td>2008</td>
      <td>47</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>27.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>aardsda01</td>
      <td>2009</td>
      <td>73</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>...</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1981.0</td>
      <td>28.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
merged2 = merged[merged.PA >= 434]
merged2.head()
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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>BB</th>
      <th>SO</th>
      <th>IBB</th>
      <th>HBP</th>
      <th>SH</th>
      <th>SF</th>
      <th>GIDP</th>
      <th>birthYear</th>
      <th>Age</th>
      <th>PA</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>aaronha01</td>
      <td>1954</td>
      <td>122</td>
      <td>468</td>
      <td>58</td>
      <td>131</td>
      <td>27</td>
      <td>6</td>
      <td>13</td>
      <td>69.0</td>
      <td>...</td>
      <td>28</td>
      <td>39.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>13.0</td>
      <td>1934.0</td>
      <td>20.0</td>
      <td>509.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>aaronha01</td>
      <td>1955</td>
      <td>153</td>
      <td>602</td>
      <td>105</td>
      <td>189</td>
      <td>37</td>
      <td>9</td>
      <td>27</td>
      <td>106.0</td>
      <td>...</td>
      <td>49</td>
      <td>61.0</td>
      <td>5.0</td>
      <td>3.0</td>
      <td>7.0</td>
      <td>4.0</td>
      <td>20.0</td>
      <td>1934.0</td>
      <td>21.0</td>
      <td>665.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>aaronha01</td>
      <td>1956</td>
      <td>153</td>
      <td>609</td>
      <td>106</td>
      <td>200</td>
      <td>34</td>
      <td>14</td>
      <td>26</td>
      <td>92.0</td>
      <td>...</td>
      <td>37</td>
      <td>54.0</td>
      <td>6.0</td>
      <td>2.0</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>21.0</td>
      <td>1934.0</td>
      <td>22.0</td>
      <td>660.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>aaronha01</td>
      <td>1957</td>
      <td>151</td>
      <td>615</td>
      <td>118</td>
      <td>198</td>
      <td>27</td>
      <td>6</td>
      <td>44</td>
      <td>132.0</td>
      <td>...</td>
      <td>57</td>
      <td>58.0</td>
      <td>15.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>13.0</td>
      <td>1934.0</td>
      <td>23.0</td>
      <td>675.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>aaronha01</td>
      <td>1958</td>
      <td>153</td>
      <td>601</td>
      <td>109</td>
      <td>196</td>
      <td>34</td>
      <td>4</td>
      <td>30</td>
      <td>95.0</td>
      <td>...</td>
      <td>59</td>
      <td>49.0</td>
      <td>16.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>21.0</td>
      <td>1934.0</td>
      <td>24.0</td>
      <td>664.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
sns.distplot(merged2['H'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1f831d1cac8>




![png](output_19_1.png)



```python
merged2['S%'] = (merged2['H']-merged2['2B']-merged2['3B']-merged2['HR'])/merged2['PA']
merged2['2B%'] = merged2['2B']/merged2['PA']
merged2['3B%'] = merged2['3B']/merged2['PA']
merged2['HR%'] = merged2['HR']/merged2['PA']
merged2['BB%'] = merged2['BB']/merged2['PA']
merged2['K%'] = merged2['SO']/merged2['PA']
merged2['SB%'] = merged2['SB']/(merged2['SB']+merged2['CS'])
merged2.head()
```

    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """Entry point for launching an IPython kernel.
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:3: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      This is separate from the ipykernel package so we can avoid doing imports until
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:4: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      after removing the cwd from sys.path.
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:5: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:6: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      
    C:\Users\ben16\Anaconda3\lib\site-packages\ipykernel_launcher.py:7: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      import sys
    




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
      <th>playerID</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>birthYear</th>
      <th>Age</th>
      <th>PA</th>
      <th>S%</th>
      <th>2B%</th>
      <th>3B%</th>
      <th>HR%</th>
      <th>BB%</th>
      <th>K%</th>
      <th>SB%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>aaronha01</td>
      <td>1954</td>
      <td>122</td>
      <td>468</td>
      <td>58</td>
      <td>131</td>
      <td>27</td>
      <td>6</td>
      <td>13</td>
      <td>69.0</td>
      <td>...</td>
      <td>1934.0</td>
      <td>20.0</td>
      <td>509.0</td>
      <td>0.166994</td>
      <td>0.053045</td>
      <td>0.011788</td>
      <td>0.025540</td>
      <td>0.055010</td>
      <td>0.076621</td>
      <td>0.500000</td>
    </tr>
    <tr>
      <th>10</th>
      <td>aaronha01</td>
      <td>1955</td>
      <td>153</td>
      <td>602</td>
      <td>105</td>
      <td>189</td>
      <td>37</td>
      <td>9</td>
      <td>27</td>
      <td>106.0</td>
      <td>...</td>
      <td>1934.0</td>
      <td>21.0</td>
      <td>665.0</td>
      <td>0.174436</td>
      <td>0.055639</td>
      <td>0.013534</td>
      <td>0.040602</td>
      <td>0.073684</td>
      <td>0.091729</td>
      <td>0.750000</td>
    </tr>
    <tr>
      <th>11</th>
      <td>aaronha01</td>
      <td>1956</td>
      <td>153</td>
      <td>609</td>
      <td>106</td>
      <td>200</td>
      <td>34</td>
      <td>14</td>
      <td>26</td>
      <td>92.0</td>
      <td>...</td>
      <td>1934.0</td>
      <td>22.0</td>
      <td>660.0</td>
      <td>0.190909</td>
      <td>0.051515</td>
      <td>0.021212</td>
      <td>0.039394</td>
      <td>0.056061</td>
      <td>0.081818</td>
      <td>0.333333</td>
    </tr>
    <tr>
      <th>12</th>
      <td>aaronha01</td>
      <td>1957</td>
      <td>151</td>
      <td>615</td>
      <td>118</td>
      <td>198</td>
      <td>27</td>
      <td>6</td>
      <td>44</td>
      <td>132.0</td>
      <td>...</td>
      <td>1934.0</td>
      <td>23.0</td>
      <td>675.0</td>
      <td>0.179259</td>
      <td>0.040000</td>
      <td>0.008889</td>
      <td>0.065185</td>
      <td>0.084444</td>
      <td>0.085926</td>
      <td>0.500000</td>
    </tr>
    <tr>
      <th>13</th>
      <td>aaronha01</td>
      <td>1958</td>
      <td>153</td>
      <td>601</td>
      <td>109</td>
      <td>196</td>
      <td>34</td>
      <td>4</td>
      <td>30</td>
      <td>95.0</td>
      <td>...</td>
      <td>1934.0</td>
      <td>24.0</td>
      <td>664.0</td>
      <td>0.192771</td>
      <td>0.051205</td>
      <td>0.006024</td>
      <td>0.045181</td>
      <td>0.088855</td>
      <td>0.073795</td>
      <td>0.800000</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 29 columns</p>
</div>




```python
y = merged2['playerID'].tolist()
z = np.unique(y)
len(z)
```




    3074




```python
dS = []
d2B = []
d3B = []
dHR = []
dBB = []
dK = []
dSB = []
age = []
stats = ['S%', '2B%', '3B%', 'HR%', 'BB%', 'K%', 'SB%']
dstats = {'S%': dS, '2B%': d2B, '3B%': d3B, 'HR%': dHR, 'BB%': dBB, 'K%': dK, 'SB%': dSB}
m = 0
for player in z:
    m +=1
    n = 0
    temp = merged2[merged2.playerID == player]
    for i in stats:
        stat = []
        peak = []
        for index, row in temp.iterrows():
            stat.append(row[i])
            if n == 0:
                age.append(row['Age'])
        n +=1
        sd = np.std(stat)
        mean = np.mean(stat)
        most = max(stat)
        for j in stat:
            if j >= most - 2*sd:
                peak.append(j)
            pmean = np.mean(stat)
        for k in stat:
            dstats[i].append(k-pmean)
    if m % 500 == 0:
        print(m)
```

    500
    1000
    1500
    2000
    2500
    3000
    


```python
avgG = np.mean(merged2['G'])
avgAB = np.mean(merged2['AB'])
avgPA = np.mean(merged2['PA'])
```


```python
ageDF = pd.DataFrame(age, columns=['Age'])
ageDF.head(10)
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
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>25.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>26.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>27.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>28.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>29.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
ageDF['1B'] = dS
ageDF['2B'] = d2B
ageDF['3B'] = d3B
ageDF['HR'] = dHR
ageDF['BB'] = dBB
ageDF['K'] = dK
ageDF['SB'] = dSB
ageDF.head(10)
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
      <th>Age</th>
      <th>1B</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>BB</th>
      <th>K</th>
      <th>SB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20.0</td>
      <td>0.002238</td>
      <td>0.008352</td>
      <td>0.004568</td>
      <td>-0.029236</td>
      <td>-0.046549</td>
      <td>-0.022406</td>
      <td>-0.188643</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21.0</td>
      <td>0.009680</td>
      <td>0.010945</td>
      <td>0.006314</td>
      <td>-0.014175</td>
      <td>-0.027874</td>
      <td>-0.007297</td>
      <td>0.061357</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22.0</td>
      <td>0.026153</td>
      <td>0.006822</td>
      <td>0.013992</td>
      <td>-0.015383</td>
      <td>-0.045498</td>
      <td>-0.017208</td>
      <td>-0.355310</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.0</td>
      <td>0.014503</td>
      <td>-0.004694</td>
      <td>0.001669</td>
      <td>0.010408</td>
      <td>-0.017114</td>
      <td>-0.013101</td>
      <td>-0.188643</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.0</td>
      <td>0.028015</td>
      <td>0.006511</td>
      <td>-0.001196</td>
      <td>-0.009596</td>
      <td>-0.012703</td>
      <td>-0.025231</td>
      <td>0.111357</td>
    </tr>
    <tr>
      <th>5</th>
      <td>25.0</td>
      <td>0.024277</td>
      <td>0.021684</td>
      <td>0.002881</td>
      <td>0.001500</td>
      <td>-0.027966</td>
      <td>-0.021104</td>
      <td>0.311357</td>
    </tr>
    <tr>
      <th>6</th>
      <td>26.0</td>
      <td>-0.012648</td>
      <td>-0.014573</td>
      <td>0.009346</td>
      <td>0.005464</td>
      <td>-0.011197</td>
      <td>-0.004147</td>
      <td>0.007009</td>
    </tr>
    <tr>
      <th>7</th>
      <td>27.0</td>
      <td>0.005139</td>
      <td>0.013429</td>
      <td>0.007683</td>
      <td>-0.004106</td>
      <td>-0.018101</td>
      <td>-0.003646</td>
      <td>0.011357</td>
    </tr>
    <tr>
      <th>8</th>
      <td>28.0</td>
      <td>0.003160</td>
      <td>-0.002715</td>
      <td>0.001775</td>
      <td>0.012690</td>
      <td>-0.002608</td>
      <td>0.010419</td>
      <td>-0.006825</td>
    </tr>
    <tr>
      <th>9</th>
      <td>29.0</td>
      <td>0.008913</td>
      <td>-0.004077</td>
      <td>-0.001618</td>
      <td>0.006848</td>
      <td>0.007685</td>
      <td>0.032626</td>
      <td>0.172468</td>
    </tr>
  </tbody>
</table>
</div>




```python
agesDF = ageDF.groupby(['Age'], as_index=False).mean()
agesDF.head(10)
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
      <th>Age</th>
      <th>1B</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>BB</th>
      <th>K</th>
      <th>SB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19.0</td>
      <td>0.003098</td>
      <td>-0.002313</td>
      <td>0.001608</td>
      <td>-0.005225</td>
      <td>-0.029036</td>
      <td>0.000659</td>
      <td>-0.065873</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>0.003661</td>
      <td>-0.003262</td>
      <td>0.000880</td>
      <td>-0.007633</td>
      <td>-0.015165</td>
      <td>0.009343</td>
      <td>-0.034077</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.0</td>
      <td>0.005650</td>
      <td>-0.002027</td>
      <td>0.002112</td>
      <td>-0.004604</td>
      <td>-0.015826</td>
      <td>0.006348</td>
      <td>-0.017295</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22.0</td>
      <td>0.000840</td>
      <td>-0.001039</td>
      <td>0.001135</td>
      <td>-0.003003</td>
      <td>-0.010342</td>
      <td>0.006738</td>
      <td>0.030409</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23.0</td>
      <td>0.002097</td>
      <td>-0.000593</td>
      <td>0.001809</td>
      <td>-0.001325</td>
      <td>-0.006883</td>
      <td>0.003593</td>
      <td>0.015740</td>
    </tr>
    <tr>
      <th>5</th>
      <td>24.0</td>
      <td>0.001862</td>
      <td>0.000153</td>
      <td>0.001142</td>
      <td>-0.001101</td>
      <td>-0.004728</td>
      <td>0.000202</td>
      <td>0.009572</td>
    </tr>
    <tr>
      <th>6</th>
      <td>25.0</td>
      <td>0.001859</td>
      <td>0.000169</td>
      <td>0.000864</td>
      <td>-0.000300</td>
      <td>-0.002965</td>
      <td>0.000255</td>
      <td>0.004725</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.0</td>
      <td>0.001265</td>
      <td>0.000442</td>
      <td>0.001009</td>
      <td>0.000147</td>
      <td>-0.001184</td>
      <td>-0.000568</td>
      <td>0.005374</td>
    </tr>
    <tr>
      <th>8</th>
      <td>27.0</td>
      <td>0.001661</td>
      <td>0.000511</td>
      <td>0.000426</td>
      <td>0.000414</td>
      <td>-0.000758</td>
      <td>-0.001375</td>
      <td>0.007496</td>
    </tr>
    <tr>
      <th>9</th>
      <td>28.0</td>
      <td>-0.000562</td>
      <td>0.000532</td>
      <td>0.000335</td>
      <td>0.000464</td>
      <td>0.000877</td>
      <td>-0.001825</td>
      <td>0.009669</td>
    </tr>
  </tbody>
</table>
</div>




```python
ageDF.groupby(['Age'], as_index=False).count()
countAge = ageDF.groupby(['Age'], as_index=False).count()['1B']
countAge
```




    0        5
    1       27
    2      109
    3      293
    4      587
    5      826
    6     1203
    7     1389
    8     1513
    9     1544
    10    1428
    11    1342
    12    1191
    13     969
    14     810
    15     663
    16     472
    17     340
    18     228
    19     134
    20      87
    21      61
    22      21
    23      13
    24       4
    25       3
    Name: 1B, dtype: int64




```python
sns.distplot(agesDF['Age'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1f8316ef7f0>




![png](output_28_1.png)



```python
agesDF2 = agesDF['Age']
agesDF2['1B'] = (total['S%'] + agesDF['1B']) * avgPA
agesDF2['2B'] = (total['2B%'] + agesDF['2B']) *avgPA
agesDF2['3B'] = (total['3B%'] + agesDF['3B']) *avgPA
agesDF2['HR'] = (total['HR%'] + agesDF['HR']) *avgPA
agesDF2['BB'] = (total['BB%'] + agesDF['BB']) *avgPA
agesDF2['K'] = (total['K%'] + agesDF['K']) *avgPA
agesDF2['SB'] = agesDF['SB']+avgSB
agesDF2.head(10)
```




    0    19
    1    20
    2    21
    3    22
    4    23
    5    24
    6    25
    7    26
    8    27
    9    28
    Name: Age, dtype: object




```python
agesDF['Single'] = (total['S%'] + agesDF['1B']) * avgPA
agesDF['Double'] = (total['2B%'] + agesDF['2B']) *avgPA
agesDF['Triple'] = (total['3B%'] + agesDF['3B']) *avgPA
agesDF['Homeruns'] = (total['HR%'] + agesDF['HR']) *avgPA
agesDF['Walks'] = (total['BB%'] + agesDF['BB']) *avgPA
agesDF['Strikeouts'] = (total['K%'] + agesDF['K']) *avgPA
agesDF['SB%'] = agesDF['SB'] + avgSB
agesDF.head()
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
      <th>Age</th>
      <th>1B</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>BB</th>
      <th>K</th>
      <th>SB</th>
      <th>Single</th>
      <th>Double</th>
      <th>Triple</th>
      <th>Homeruns</th>
      <th>Walks</th>
      <th>Strikeouts</th>
      <th>SB%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19.0</td>
      <td>0.003098</td>
      <td>-0.002313</td>
      <td>0.001608</td>
      <td>-0.005225</td>
      <td>-0.029036</td>
      <td>0.000659</td>
      <td>-0.065873</td>
      <td>109.301813</td>
      <td>24.709295</td>
      <td>5.742622</td>
      <td>9.401928</td>
      <td>32.984456</td>
      <td>83.481706</td>
      <td>0.653484</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>0.003661</td>
      <td>-0.003262</td>
      <td>0.000880</td>
      <td>-0.007633</td>
      <td>-0.015165</td>
      <td>0.009343</td>
      <td>-0.034077</td>
      <td>109.626716</td>
      <td>24.161903</td>
      <td>5.322693</td>
      <td>8.012992</td>
      <td>40.986932</td>
      <td>88.491935</td>
      <td>0.685280</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.0</td>
      <td>0.005650</td>
      <td>-0.002027</td>
      <td>0.002112</td>
      <td>-0.004604</td>
      <td>-0.015826</td>
      <td>0.006348</td>
      <td>-0.017295</td>
      <td>110.774459</td>
      <td>24.874396</td>
      <td>6.033803</td>
      <td>9.760404</td>
      <td>40.605560</td>
      <td>86.763735</td>
      <td>0.702061</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22.0</td>
      <td>0.000840</td>
      <td>-0.001039</td>
      <td>0.001135</td>
      <td>-0.003003</td>
      <td>-0.010342</td>
      <td>0.006738</td>
      <td>0.030409</td>
      <td>107.999096</td>
      <td>25.444103</td>
      <td>5.470172</td>
      <td>10.683883</td>
      <td>43.769450</td>
      <td>86.989266</td>
      <td>0.749766</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23.0</td>
      <td>0.002097</td>
      <td>-0.000593</td>
      <td>0.001809</td>
      <td>-0.001325</td>
      <td>-0.006883</td>
      <td>0.003593</td>
      <td>0.015740</td>
      <td>108.724601</td>
      <td>25.701742</td>
      <td>5.858604</td>
      <td>11.652051</td>
      <td>45.765342</td>
      <td>85.174792</td>
      <td>0.735097</td>
    </tr>
  </tbody>
</table>
</div>




```python
agesDF['Count'] = countAge
agesDF.head()
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
      <th>Age</th>
      <th>1B</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>BB</th>
      <th>K</th>
      <th>SB</th>
      <th>Single</th>
      <th>Double</th>
      <th>Triple</th>
      <th>Homeruns</th>
      <th>Walks</th>
      <th>Strikeouts</th>
      <th>SB%</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19.0</td>
      <td>0.003098</td>
      <td>-0.002313</td>
      <td>0.001608</td>
      <td>-0.005225</td>
      <td>-0.029036</td>
      <td>0.000659</td>
      <td>-0.065873</td>
      <td>109.301813</td>
      <td>24.709295</td>
      <td>5.742622</td>
      <td>9.401928</td>
      <td>32.984456</td>
      <td>83.481706</td>
      <td>0.653484</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>0.003661</td>
      <td>-0.003262</td>
      <td>0.000880</td>
      <td>-0.007633</td>
      <td>-0.015165</td>
      <td>0.009343</td>
      <td>-0.034077</td>
      <td>109.626716</td>
      <td>24.161903</td>
      <td>5.322693</td>
      <td>8.012992</td>
      <td>40.986932</td>
      <td>88.491935</td>
      <td>0.685280</td>
      <td>27</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.0</td>
      <td>0.005650</td>
      <td>-0.002027</td>
      <td>0.002112</td>
      <td>-0.004604</td>
      <td>-0.015826</td>
      <td>0.006348</td>
      <td>-0.017295</td>
      <td>110.774459</td>
      <td>24.874396</td>
      <td>6.033803</td>
      <td>9.760404</td>
      <td>40.605560</td>
      <td>86.763735</td>
      <td>0.702061</td>
      <td>109</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22.0</td>
      <td>0.000840</td>
      <td>-0.001039</td>
      <td>0.001135</td>
      <td>-0.003003</td>
      <td>-0.010342</td>
      <td>0.006738</td>
      <td>0.030409</td>
      <td>107.999096</td>
      <td>25.444103</td>
      <td>5.470172</td>
      <td>10.683883</td>
      <td>43.769450</td>
      <td>86.989266</td>
      <td>0.749766</td>
      <td>293</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23.0</td>
      <td>0.002097</td>
      <td>-0.000593</td>
      <td>0.001809</td>
      <td>-0.001325</td>
      <td>-0.006883</td>
      <td>0.003593</td>
      <td>0.015740</td>
      <td>108.724601</td>
      <td>25.701742</td>
      <td>5.858604</td>
      <td>11.652051</td>
      <td>45.765342</td>
      <td>85.174792</td>
      <td>0.735097</td>
      <td>587</td>
    </tr>
  </tbody>
</table>
</div>




```python
totalAge = merged2.groupby(['Age'], as_index=False).sum()
totalAge.head()
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
      <th>Age</th>
      <th>yearID</th>
      <th>G</th>
      <th>AB</th>
      <th>R</th>
      <th>H</th>
      <th>2B</th>
      <th>3B</th>
      <th>HR</th>
      <th>RBI</th>
      <th>...</th>
      <th>GIDP</th>
      <th>birthYear</th>
      <th>PA</th>
      <th>S%</th>
      <th>2B%</th>
      <th>3B%</th>
      <th>HR%</th>
      <th>BB%</th>
      <th>K%</th>
      <th>SB%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19.0</td>
      <td>9735</td>
      <td>660</td>
      <td>2386</td>
      <td>313</td>
      <td>643</td>
      <td>100</td>
      <td>27</td>
      <td>58</td>
      <td>310.0</td>
      <td>...</td>
      <td>43.0</td>
      <td>9640.0</td>
      <td>2663.0</td>
      <td>0.860076</td>
      <td>0.188519</td>
      <td>0.048246</td>
      <td>0.116969</td>
      <td>0.419361</td>
      <td>0.498989</td>
      <td>2.866667</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20.0</td>
      <td>52959</td>
      <td>3668</td>
      <td>13434</td>
      <td>1849</td>
      <td>3687</td>
      <td>614</td>
      <td>138</td>
      <td>294</td>
      <td>1616.0</td>
      <td>...</td>
      <td>233.0</td>
      <td>52419.0</td>
      <td>14929.0</td>
      <td>4.777158</td>
      <td>1.103403</td>
      <td>0.247244</td>
      <td>0.526140</td>
      <td>2.110696</td>
      <td>3.275137</td>
      <td>17.966991</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.0</td>
      <td>213594</td>
      <td>15136</td>
      <td>56053</td>
      <td>7920</td>
      <td>15834</td>
      <td>2566</td>
      <td>706</td>
      <td>1257</td>
      <td>6917.0</td>
      <td>...</td>
      <td>887.0</td>
      <td>211305.0</td>
      <td>62243.0</td>
      <td>19.665723</td>
      <td>4.445627</td>
      <td>1.229692</td>
      <td>2.156063</td>
      <td>8.237987</td>
      <td>12.779904</td>
      <td>70.513448</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22.0</td>
      <td>574005</td>
      <td>41243</td>
      <td>152644</td>
      <td>21094</td>
      <td>41993</td>
      <td>7090</td>
      <td>1727</td>
      <td>3262</td>
      <td>18414.0</td>
      <td>...</td>
      <td>2275.0</td>
      <td>567559.0</td>
      <td>170103.0</td>
      <td>51.384986</td>
      <td>12.133556</td>
      <td>2.931137</td>
      <td>5.494268</td>
      <td>23.040643</td>
      <td>34.157131</td>
      <td>205.894467</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23.0</td>
      <td>1152400</td>
      <td>82073</td>
      <td>300355</td>
      <td>42031</td>
      <td>83573</td>
      <td>14390</td>
      <td>3519</td>
      <td>7146</td>
      <td>38306.0</td>
      <td>...</td>
      <td>4774.0</td>
      <td>1138899.0</td>
      <td>335784.0</td>
      <td>101.997909</td>
      <td>24.943715</td>
      <td>6.116340</td>
      <td>12.241984</td>
      <td>48.124398</td>
      <td>71.506107</td>
      <td>402.038828</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 28 columns</p>
</div>




```python
plt.pie(totalAge['AB'], labels=totalAge['Age'], autopct="%1.1f%%", shadow=True, startangle=140, radius = 5)
plt.show()
```


![png](output_33_0.png)



```python
a4_dims = (10, 10)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Strikeouts', data=agesDF, ax=ax)
plt.title('HR vs Age', fontsize = 20)
plt.xlabel('Age', fontsize = 20)
plt.xlabel('Strikeouts', fontsize = 20)
```




    Text(0.5,0,'Age')




![png](output_34_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Single', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('Singles vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Singles', fontsize = 20)
```




    Text(0,0.5,'Singles')




![png](output_35_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Double', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('Doubles vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Doubles', fontsize = 20)
```




    Text(0,0.5,'Doubles')




![png](output_36_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Triple', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('Triples vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Triples', fontsize = 20)
```




    Text(0,0.5,'Triples')




![png](output_37_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Homeruns', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('HR vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Homeruns', fontsize = 20)
```




    Text(0,0.5,'Homeruns')




![png](output_38_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Walks', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('Walks vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Walks', fontsize = 20)
```




    Text(0,0.5,'Walks')




![png](output_39_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='Strikeouts', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('Strikeouts vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('Strikeouts', fontsize = 20)
```




    Text(0,0.5,'Strikeouts')




![png](output_40_1.png)



```python
a4_dims = (20, 20)
fig, ax = plt.subplots(figsize=a4_dims)
sns.regplot(x='Age',y='SB%', data=agesDF, ax=ax,scatter_kws={"s": 10*agesDF['Count']**(4/5)},order=3)
plt.title('SB% vs Age', fontsize = 40)
plt.xlabel('Age', fontsize = 20)
plt.ylabel('SB%', fontsize = 20)
```




    Text(0,0.5,'SB%')




![png](output_41_1.png)



```python
l = np.polyfit(agesDF['Age'], agesDF['Walks'], 1)
print(f'y = {l[0]}x + {l[1]}')
```

    y = 0.5505199607079446x + 31.807096597474672
    


```python
l = np.polyfit(agesDF['Age'], agesDF['Walks'], 0)
l
```




    array([49.14847536])


