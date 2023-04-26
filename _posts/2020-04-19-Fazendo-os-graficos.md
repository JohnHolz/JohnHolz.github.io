```python
from selenium import webdriver
import pandas as pd, seaborn as sns, matplotlib.pyplot as plt
import time 
import warnings
warnings.filterwarnings("ignore")
```


```python
site = "http://www.obt.inpe.br/OBT/assuntos/programas/amazonia/prodes"
df = pd.DataFrame(pd.read_html(site)[1])
new_header = df.iloc[0] 
df = df[1:-2]
df.columns = new_header
df.index = df.iloc[:,0]
df = df.drop(['Ano/Estados'],axis=1)
df = df.apply(pd.to_numeric)
```


```python
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
      <th>estado</th>
      <th>AC</th>
      <th>AM</th>
      <th>AP</th>
      <th>MA</th>
      <th>MT</th>
      <th>PA</th>
      <th>RO</th>
      <th>RR</th>
      <th>TO</th>
      <th>AMZ LEGAL</th>
    </tr>
    <tr>
      <th>Ano/Estados</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1988</th>
      <td>620</td>
      <td>1510</td>
      <td>60</td>
      <td>2450</td>
      <td>5140</td>
      <td>6990</td>
      <td>2340</td>
      <td>290</td>
      <td>1650</td>
      <td>21050</td>
    </tr>
    <tr>
      <th>1989</th>
      <td>540</td>
      <td>1180</td>
      <td>130</td>
      <td>1420</td>
      <td>5960</td>
      <td>5750</td>
      <td>1430</td>
      <td>630</td>
      <td>730</td>
      <td>17770</td>
    </tr>
    <tr>
      <th>1990</th>
      <td>550</td>
      <td>520</td>
      <td>250</td>
      <td>1100</td>
      <td>4020</td>
      <td>4890</td>
      <td>1670</td>
      <td>150</td>
      <td>580</td>
      <td>13730</td>
    </tr>
    <tr>
      <th>1991</th>
      <td>380</td>
      <td>980</td>
      <td>410</td>
      <td>670</td>
      <td>2840</td>
      <td>3780</td>
      <td>1110</td>
      <td>420</td>
      <td>440</td>
      <td>11030</td>
    </tr>
    <tr>
      <th>1992</th>
      <td>400</td>
      <td>799</td>
      <td>36</td>
      <td>1135</td>
      <td>4674</td>
      <td>3787</td>
      <td>2265</td>
      <td>281</td>
      <td>409</td>
      <td>13786</td>
    </tr>
  </tbody>
</table>
</div>




```python
_ = plt.title('Proporção (1988-2021)',fontsize=18)
_ = plt.pie(df.iloc[:,:-1].sum(),labels=df.iloc[:,:-1].columns)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_3_0.png)
    



```python
_ = plt.title('Proporção (1988-1998)',fontsize=18)
_ = plt.pie(df.iloc[:10,:-1].sum(),labels=df.iloc[:,:-1].columns)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_4_0.png)
    



```python
_ = df.plot(marker='o')
_ = plt.legend(title="")
_ = plt.title('Amazônia Legal - Desmatamento por estado e Ano (km²)',fontsize=18)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_5_0.png)
    



```python
_ = df.cumsum().plot(marker='')
_ = plt.legend(title="")
_ = plt.title('Acumulado por estado e Ano - desde 1988 (km²)',fontsize=18)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_6_0.png)
    



```python
import geopandas as gpd, geobr as gbr
```


```python
estados = gbr.read_state()
to_merge = pd.DataFrame(df.sum())
to_merge.columns = ['desmatamento']
to_merge.index.name = 'estado'
estados = estados.join(to_merge,on='abbrev_state')
estados = estados.dropna()
```


```python
estados.head().iloc[:,[1,2,3,4,6]]
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
      <th>abbrev_state</th>
      <th>name_state</th>
      <th>code_region</th>
      <th>name_region</th>
      <th>desmatamento</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>RO</td>
      <td>Rondônia</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>23153.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AC</td>
      <td>Acre</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>5453.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AM</td>
      <td>Amazonas</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>9455.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>RR</td>
      <td>Roraima</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>2869.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>PA</td>
      <td>Pará</td>
      <td>1.0</td>
      <td>Norte</td>
      <td>51884.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
f, ax = plt.subplots()
_ = f.set_size_inches(16, 16)
_ = estados.plot(ax = ax,
             column= 'desmatamento',
             cmap="Reds",
             edgecolor="black",
             linewidth=0.25)
_ = plt.title('Total Acumulado',fontsize=22)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_10_0.png)
    



```python
estados = gbr.read_state()
to_merge = pd.DataFrame(df.iloc[:10,:].sum())
to_merge.columns = ['desmatamento']
to_merge.index.name = 'estado'
estados = estados.join(to_merge,on='abbrev_state')
estados = estados.dropna()

f, ax = plt.subplots()
_ = f.set_size_inches(16, 16)
_ = estados.plot(ax = ax,
             column= 'desmatamento',
             cmap="Reds",
             edgecolor="black",
            linewidth=0.25)
_ = plt.title('Primeiros 10 anos (1988-1998)',fontsize=22)
```


    
![png](https://raw.githubusercontent.com/JohnHolz/JohnHolz.github.io/master/_posts/images/output_11_0.png)
    



```python

```
