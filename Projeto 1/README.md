# Relatorio analise 1
Neste relatorio, foi feita uma analise exploratoria para descobrir o que continha estes dados.
Contem uma base com informações de imóveis e bairros do rio de janeiro.
Ao adicionar outros relatorios de analise, irei adicionar outros arquivos ".md" para visualização.

## Importando base de dados

```python
import pandas as pd
```


```python
# Importando dados para primeira visualização
pd.read_csv("dados/aluguel.csv", sep = ';')
```

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
      <td>Conjunto Comercial/Sala</td>
      <td>Barra da Tijuca</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>150</td>
      <td>5200.0</td>
      <td>4020.0</td>
      <td>1111.0</td>
    </tr>
    <tr>
      <th>3</th>
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
      <th>4</th>
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
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>32955</th>
      <td>Quitinete</td>
      <td>Centro</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>27</td>
      <td>800.0</td>
      <td>350.0</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>32956</th>
      <td>Apartamento</td>
      <td>Jacarepaguá</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>78</td>
      <td>1800.0</td>
      <td>800.0</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>32957</th>
      <td>Apartamento</td>
      <td>São Francisco Xavier</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>48</td>
      <td>1400.0</td>
      <td>509.0</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>32958</th>
      <td>Apartamento</td>
      <td>Leblon</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>3000.0</td>
      <td>760.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32959</th>
      <td>Conjunto Comercial/Sala</td>
      <td>Centro</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>250</td>
      <td>6500.0</td>
      <td>4206.0</td>
      <td>1109.0</td>
    </tr>
  </tbody>
</table>
<p>32960 rows × 9 columns</p>
</div>




```python
# Salvando dados em variaveis
dados = pd.read_csv('dados/aluguel.csv', sep = ';')
```


```python
# Verificando se a importacao foi correta em uma variavel
dados
```


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
      <td>Conjunto Comercial/Sala</td>
      <td>Barra da Tijuca</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>150</td>
      <td>5200.0</td>
      <td>4020.0</td>
      <td>1111.0</td>
    </tr>
    <tr>
      <th>3</th>
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
      <th>4</th>
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
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>32955</th>
      <td>Quitinete</td>
      <td>Centro</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>27</td>
      <td>800.0</td>
      <td>350.0</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>32956</th>
      <td>Apartamento</td>
      <td>Jacarepaguá</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>78</td>
      <td>1800.0</td>
      <td>800.0</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>32957</th>
      <td>Apartamento</td>
      <td>São Francisco Xavier</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>48</td>
      <td>1400.0</td>
      <td>509.0</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>32958</th>
      <td>Apartamento</td>
      <td>Leblon</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>3000.0</td>
      <td>760.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32959</th>
      <td>Conjunto Comercial/Sala</td>
      <td>Centro</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>250</td>
      <td>6500.0</td>
      <td>4206.0</td>
      <td>1109.0</td>
    </tr>
  </tbody>
</table>
<p>32960 rows × 9 columns</p>
</div>




```python
# Verificando tipo de variavel
type(dados)
```




    pandas.core.frame.DataFrame




```python
# Verificando info para melhor visualizar as colucas e tipos de objetos
dados.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 32960 entries, 0 to 32959
    Data columns (total 9 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   Tipo        32960 non-null  object 
     1   Bairro      32960 non-null  object 
     2   Quartos     32960 non-null  int64  
     3   Vagas       32960 non-null  int64  
     4   Suites      32960 non-null  int64  
     5   Area        32960 non-null  int64  
     6   Valor       32943 non-null  float64
     7   Condominio  28867 non-null  float64
     8   IPTU        22723 non-null  float64
    dtypes: float64(3), int64(4), object(2)
    memory usage: 2.3+ MB
    


```python
# Usado para verificar apenas os 10 primeiros resultados
dados.head(10)
```


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
      <td>Conjunto Comercial/Sala</td>
      <td>Barra da Tijuca</td>
      <td>0</td>
      <td>4</td>
      <td>0</td>
      <td>150</td>
      <td>5200.0</td>
      <td>4020.0</td>
      <td>1111.0</td>
    </tr>
    <tr>
      <th>3</th>
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
      <th>4</th>
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
      <th>5</th>
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
      <th>6</th>
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
      <th>7</th>
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
      <th>8</th>
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
      <th>9</th>
      <td>Conjunto Comercial/Sala</td>
      <td>Centro</td>
      <td>0</td>
      <td>3</td>
      <td>0</td>
      <td>695</td>
      <td>35000.0</td>
      <td>19193.0</td>
      <td>3030.0</td>
    </tr>
  </tbody>
</table>
</div>



## informacoes gerais sobre a base de dados


```python
dados.dtypes
```




    Tipo           object
    Bairro         object
    Quartos         int64
    Vagas           int64
    Suites          int64
    Area            int64
    Valor         float64
    Condominio    float64
    IPTU          float64
    dtype: object




```python
# Usado para informar os tipos de dados
tipos_de_dados = pd.DataFrame(dados.dtypes, columns = ['Tipos de dados'])
```


```python
# usado para adicionar um nome as colunas
tipos_de_dados.columns.name = 'Variaveis'
```


```python
tipos_de_dados
```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Variaveis</th>
      <th>Tipos de dados</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tipo</th>
      <td>object</td>
    </tr>
    <tr>
      <th>Bairro</th>
      <td>object</td>
    </tr>
    <tr>
      <th>Quartos</th>
      <td>int64</td>
    </tr>
    <tr>
      <th>Vagas</th>
      <td>int64</td>
    </tr>
    <tr>
      <th>Suites</th>
      <td>int64</td>
    </tr>
    <tr>
      <th>Area</th>
      <td>int64</td>
    </tr>
    <tr>
      <th>Valor</th>
      <td>float64</td>
    </tr>
    <tr>
      <th>Condominio</th>
      <td>float64</td>
    </tr>
    <tr>
      <th>IPTU</th>
      <td>float64</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados.shape
```




    (32960, 9)




```python
dados.shape[0]
```




    32960




```python
dados.shape[1]
```




    9




```python
print('A base de dados aprensenta {} registros (imóveis) e {} variaveis'.format(dados.shape[0],dados.shape[1]))
```

    A base de dados aprensenta 32960 registros (imóveis) e 9 variaveis
    
