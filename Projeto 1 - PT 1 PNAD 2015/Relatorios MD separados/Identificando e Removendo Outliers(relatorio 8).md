# Relatorio de analise 8

## Identificando e removendo outliers


```python
%matplotlib inline
import pandas as pd
import matplotlib.pyplot as plt
plt.rc('figure', figsize = (14,6))
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep=';')
dados.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo</th>
      <th>Bairro</th>
      <th>Quartos</th>
      <th>Vagas</th>
      <th>Suites</th>
      <th>Area</th>
      <th>Valor</th>
      <th>Condominio</th>
      <th>IPTU</th>
      <th>Valor m2</th>
      <th>Tipo Agregado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Quitinete</td>
      <td>Copacabana</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>40</td>
      <td>1700.0</td>
      <td>500.0</td>
      <td>60.0</td>
      <td>42.50</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
      <td>Jardim Botânico</td>
      <td>2</td>
      <td>0</td>
      <td>1</td>
      <td>100</td>
      <td>7000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>70.00</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Apartamento</td>
      <td>Centro</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>800.0</td>
      <td>390.0</td>
      <td>20.0</td>
      <td>53.33</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
      <td>Higienópolis</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>48</td>
      <td>800.0</td>
      <td>230.0</td>
      <td>0.0</td>
      <td>16.67</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Apartamento</td>
      <td>Cachambi</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>1300.0</td>
      <td>301.0</td>
      <td>17.0</td>
      <td>26.00</td>
      <td>Apartamento</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados['Valor'].describe()
```




    count    2.182600e+04
    mean     5.046173e+03
    std      3.298854e+04
    min      1.000000e+02
    25%      1.600000e+03
    50%      2.700000e+03
    75%      5.500000e+03
    max      4.500000e+06
    Name: Valor, dtype: float64




```python
dados.boxplot(['Valor'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x21071554708>




![png](output_5_1.png)



```python
dados[dados['Valor'] >= 500000]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo</th>
      <th>Bairro</th>
      <th>Quartos</th>
      <th>Vagas</th>
      <th>Suites</th>
      <th>Area</th>
      <th>Valor</th>
      <th>Condominio</th>
      <th>IPTU</th>
      <th>Valor m2</th>
      <th>Tipo Agregado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7629</th>
      <td>Apartamento</td>
      <td>Barra da Tijuca</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>65</td>
      <td>600000.0</td>
      <td>980.0</td>
      <td>120.0</td>
      <td>9230.77</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>10636</th>
      <td>Casa de Condomínio</td>
      <td>Freguesia (Jacarepaguá)</td>
      <td>4</td>
      <td>2</td>
      <td>3</td>
      <td>163</td>
      <td>800000.0</td>
      <td>900.0</td>
      <td>0.0</td>
      <td>4907.98</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>12661</th>
      <td>Apartamento</td>
      <td>Freguesia (Jacarepaguá)</td>
      <td>2</td>
      <td>2</td>
      <td>1</td>
      <td>150</td>
      <td>550000.0</td>
      <td>850.0</td>
      <td>150.0</td>
      <td>3666.67</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>13846</th>
      <td>Apartamento</td>
      <td>Recreio dos Bandeirantes</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>167</td>
      <td>1250000.0</td>
      <td>1186.0</td>
      <td>320.0</td>
      <td>7485.03</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>15520</th>
      <td>Apartamento</td>
      <td>Botafogo</td>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>300</td>
      <td>4500000.0</td>
      <td>1100.0</td>
      <td>0.0</td>
      <td>15000.00</td>
      <td>Apartamento</td>
    </tr>
  </tbody>
</table>
</div>




```python
valor = dados['Valor']
q1 = valor.quantile(.25)
q3 = valor.quantile(.75)
iiq = q3 - q1 # Intervalo inter quartio
limite_inferior = q1 - 1.5 * iiq
limite_superior = q3 + 1.5 * iiq
```


```python
selecao = (valor >= limite_inferior) & (valor <= limite_superior)
dados_new = dados[selecao]
dados_new.boxplot(['Valor'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2107180fcc8>




![png](output_8_1.png)



```python
# como nossos dados possuem valores discrepantes, tivemos que usar essa formula do boxplot para calcular a margem
# sem os valores discrepantes (eles ficam armazenados em outro local por assim dizer)
```


```python
# para mostrar em um histograma essas informacoes, iremos usar o antes e o depois
dados.hist(['Valor'])
dados_new.hist(['Valor'])
```




    array([[<matplotlib.axes._subplots.AxesSubplot object at 0x0000021071678608>]],
          dtype=object)




![png](output_10_1.png)



![png](output_10_2.png)


## Continuacao


```python
dados.boxplot(['Valor'], by = ['Tipo'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x21071cfc5c8>




![png](output_12_1.png)



```python
grupo_tipo = dados.groupby('Tipo')['Valor']
```


```python
type(grupo_tipo)
```




    pandas.core.groupby.generic.SeriesGroupBy




```python
grupo_tipo.groups
```




    {'Apartamento': Int64Index([    2,     3,     4,     7,     8,     9,    11,    13,    14,
                    15,
                 ...
                 21813, 21814, 21816, 21817, 21818, 21819, 21821, 21823, 21824,
                 21825],
                dtype='int64', length=18780),
     'Casa': Int64Index([    1,    22,    54,    57,    96,   100,   144,   160,   180,
                   238,
                 ...
                 21582, 21606, 21614, 21667, 21672, 21699, 21756, 21781, 21793,
                 21804],
                dtype='int64', length=965),
     'Casa de Condomínio': Int64Index([    5,     6,    12,    16,    42,    58,   166,   168,   183,
                   207,
                 ...
                 21709, 21711, 21719, 21752, 21763, 21764, 21782, 21791, 21801,
                 21820],
                dtype='int64', length=996),
     'Casa de Vila': Int64Index([   81,   212,   220,   303,   332,   697,   822,   844,   918,
                  1012,
                 ...
                 21184, 21189, 21253, 21325, 21353, 21366, 21588, 21635, 21716,
                 21762],
                dtype='int64', length=249),
     'Quitinete': Int64Index([    0,    10,    28,    71,    78,    86,   101,   120,   146,
                   174,
                 ...
                 21384, 21410, 21441, 21656, 21682, 21687, 21728, 21748, 21815,
                 21822],
                dtype='int64', length=836)}




```python
q1 = grupo_tipo.quantile(.25)
q3 = grupo_tipo.quantile(.75)
iiq = q3 - q1 # Intervalo interquartio
limite_inferior = q1 - 1.5 * iiq
limite_superior = q3 + 1.5 * iiq
```

<img src = "dados/compressed_box-plot.png" width = 70%>


```python
# A intenção desse for abaixo, é realizar uma ação de validação com o boxplot, para cada tipo separadamente
# Se simplesmente fizessemos um boxplot, iriamos receber um resultado de um modo geral, somando tudo de uma vez
# Com o for abaixo, podemos fazer a iteração dos limites para cada tipo de imóvel.

dados_new = pd.DataFrame()

for tipo in grupo_tipo.groups.keys():
    e_tipo = dados['Tipo'] == tipo
    dentro_limite = (dados['Valor'] >= limite_inferior[tipo]) & (dados['Valor'] <= limite_superior[tipo])
    selecao = e_tipo & dentro_limite
    dados_selecao = dados[selecao]
    dados_new = pd.concat([dados_new, dados_selecao])
```


```python
dados_new.boxplot(['Valor'], by = ['Tipo'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x21072161448>




![png](output_19_1.png)



```python
dados_new.to_csv('dados/aluguel_residencial_sem_outliers.csv', sep=';', index=False)
```


```python

```
