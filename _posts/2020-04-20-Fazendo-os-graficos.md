```python
from selenium import webdriver
import pandas as pd, seaborn as sns, matplotlib.pyplot as plt
import time 
import warnings
warnings.filterwarnings("ignore")

```


```python
df = pd.DataFrame(pd.read_html(site)[1])
new_header = df.iloc[0] 
df = df[1:-2]
df.columns = new_header
df.index = df.iloc[:,0]
df = df.drop(['Ano/Estados'],axis=1)
df = df.apply(pd.to_numeric)
```


```python
_ = plt.title('Acumulado Desmatamento',fontsize=18)
_ = plt.pie(df.iloc[:,:-1].sum(),labels=df.iloc[:,:-1].columns)
```


    
![png](https://github.com/JohnHolz/JohnHolz.github.io/blob/master/_posts/images/output_2_0.png)
    



```python
_ = plt.title('Amazônia Legal - 1988',fontsize=18)
_ = plt.pie(df.iloc[0,:-1],labels=df.iloc[:,:-1].columns)
```


    
![png](https://github.com/JohnHolz/JohnHolz.github.io/blob/master/_posts/images/output_3_0.png)
    



```python
_ = df.plot(marker='o')
_ = plt.legend(title="")
_ = plt.title('Amazônia Legal - Desmatamento por estado e Ano',fontsize=18)
```


    
![png](https://github.com/JohnHolz/JohnHolz.github.io/blob/master/_posts/images/output_4_0.png)
    



```python
_ = df.cumsum().plot(marker='')
_ = plt.legend(title="")
_ = plt.title('Acumulado por estado e Ano - desde 1988',fontsize=18)
```


    
![png](https://github.com/JohnHolz/JohnHolz.github.io/blob/master/_posts/images/output_5_0.png)
    



```python
import geopandas as gpd, geobr as gbr
```


```python
estados = gbr.read_state()
to_merge = pd.DataFrame(df.sum())
to_merge.columns = ['desmatamento']
to_merge.index.name = 'estado'
```


```python
estados = estados.join(to_merge,on='abbrev_state')
estados = estados.dropna()
```


```python
estados
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
      <th>code_state</th>
      <th>abbrev_state</th>
      <th>name_state</th>
      <th>code_region</th>
      <th>name_region</th>
      <th>geometry</th>
      <th>desmatamento</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11.0</td>
      <td>RO</td>
      <td>Rondônia</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-63.32721 -7.97672, -62.86662 ...</td>
      <td>64623.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>12.0</td>
      <td>AC</td>
      <td>Acre</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-73.18253 -7.33550, -72.58477 ...</td>
      <td>16668.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>13.0</td>
      <td>AM</td>
      <td>Amazonas</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-67.32609 2.02971, -67.31682 2...</td>
      <td>30790.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>14.0</td>
      <td>RR</td>
      <td>Roraima</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-60.20051 5.26434, -60.19273 5...</td>
      <td>8909.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>15.0</td>
      <td>PA</td>
      <td>Pará</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-54.95431 2.58369, -54.93542 2...</td>
      <td>162612.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>16.0</td>
      <td>AP</td>
      <td>Amapá</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-51.17970 4.00008, -51.17739 3...</td>
      <td>1656.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>17.0</td>
      <td>TO</td>
      <td>Tocantins</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>MULTIPOLYGON (((-48.35878 -5.17008, -48.33846 ...</td>
      <td>8763.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>21.0</td>
      <td>MA</td>
      <td>Maranhão</td>
      <td>2.0</td>
      <td>Nordeste</td>
      <td>MULTIPOLYGON (((-45.84073 -1.04548, -45.84099 ...</td>
      <td>26103.0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>51.0</td>
      <td>MT</td>
      <td>Mato Grosso</td>
      <td>5.0</td>
      <td>Centro Oeste</td>
      <td>MULTIPOLYGON (((-54.89485 -17.62150, -54.89704...</td>
      <td>150151.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
f, ax = plt.subplots()
_ = f.set_size_inches(16, 16)
_ = estados.plot(ax = ax,
             column= 'desmatamento',
             cmap="Greens",
             edgecolor="black",
             linewidth=0.25)
```


    
![png](https://github.com/JohnHolz/JohnHolz.github.io/blob/master/_posts/images/output_10_0.png)
    



```python

```
