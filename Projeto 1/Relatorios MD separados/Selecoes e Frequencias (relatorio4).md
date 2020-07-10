# Relatorio de analise 4

## Objetivo


```python
# Imoveis classificados por Apartamento
# Imoveis classificados como casa, casa de condominio e casa de vila
# Imoveis com area entre 60 e 100 m² incluindo os limites
# Imoveis que tenham pelo menos 4 quartos e aluguel menor que 2000
```

## Selecoes e Frequencias


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep = ';')
```


```python
dados.head(10)
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
      <td>NaN</td>
      <td>NaN</td>
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
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Apartamento</td>
      <td>Vista Alegre</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1200.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Apartamento</td>
      <td>Cachambi</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>1300.0</td>
      <td>301.0</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Casa de Condomínio</td>
      <td>Barra da Tijuca</td>
      <td>5</td>
      <td>4</td>
      <td>5</td>
      <td>750</td>
      <td>22000.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Casa de Condomínio</td>
      <td>Ramos</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>65</td>
      <td>1000.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Apartamento</td>
      <td>Centro</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>36</td>
      <td>1200.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Apartamento</td>
      <td>Grajaú</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1500.0</td>
      <td>642.0</td>
      <td>74.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Imoveis classificados por Apartamento
selecao = dados['Tipo'] == 'Apartamento'
n1 = dados[selecao].shape[0]
n1
# com isso conseguimos 19532 entradas de apartamentos
'''
para caso queiramos visualizar os apartamentos ficaria assim.
Com isso visualizariamos um dataframe dos apartamentos.
n1 = dados[selecao]
n1.index = range(n1.shape[0])
n1
'''
```




    19532




```python
# Imoveis classificados como casa, casa de condominio e casa de vila
selecao = (dados['Tipo'] == 'Casa') | (dados['Tipo'] == 'Casa de Condomínio') | (dados['Tipo'] == 'Casa de Vila')
n2 = dados[selecao].shape[0]
n2
```




    2212




```python
# Imoveis com area entre 60 e 100 m² incluindo os limites
selecao = (dados['Area'] >= 60) & (dados['Area'] <= 100)
n3 = dados[selecao].shape[0]
n3
```




    8719




```python
# Imoveis que tenham pelo menos 4 quartos e aluguel menor que 2000
selecao = (dados['Quartos'] >= 4) & (dados['Valor'] < 2000)
n4 = dados[selecao].shape[0]
n4
```




    41




```python
print("Nº de Imoveis classificados por Apartamento -> {}".format(n1))
print("Nº de Imoveis classificados como casa, casa de condominio e casa de vila -> {}".format(n2))
print("Nº de Imoveis com area entre 60 e 100 m² incluindo os limites -> {}".format(n3))
print("Nº de Imoveis que tenham pelo menos 4 quartos e aluguel menor que 2000 -> {}".format(n4))
```

    Nº de Imoveis classificados por Apartamento -> 19532
    Nº de Imoveis classificados como casa, casa de condominio e casa de vila -> 2212
    Nº de Imoveis com area entre 60 e 100 m² incluindo os limites -> 8719
    Nº de Imoveis que tenham pelo menos 4 quartos e aluguel menor que 2000 -> 41
    
