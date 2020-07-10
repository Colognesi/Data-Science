# Relatorio de analise 3

## Imoveis residenciais


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel.csv', sep=';')
```


```python
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
  </tbody>
</table>
</div>




```python
list(dados['Tipo'].drop_duplicates())
```




    ['Quitinete',
     'Casa',
     'Conjunto Comercial/Sala',
     'Apartamento',
     'Casa de Condomínio',
     'Prédio Inteiro',
     'Flat',
     'Loja/Salão',
     'Galpão/Depósito/Armazém',
     'Casa Comercial',
     'Casa de Vila',
     'Terreno Padrão',
     'Box/Garagem',
     'Loft',
     'Loja Shopping/ Ct Comercial',
     'Chácara',
     'Loteamento/Condomínio',
     'Sítio',
     'Pousada/Chalé',
     'Studio',
     'Hotel',
     'Indústria']




```python
# Sabendo os tipos de imoveis que existem na base acima, iremos criar esta variavel apenas com os residenciais.
residencial = ['Quitinete',
 'Casa',
 'Apartamento',
 'Casa de Condomínio',
 'Casa de Vila']
```


```python
residencial
```




    ['Quitinete', 'Casa', 'Apartamento', 'Casa de Condomínio', 'Casa de Vila']




```python
# agora iremos verificar quantos dos itens presentes em residencial estao na variavel dados

selecao = dados['Tipo'].isin(residencial)
```


```python
# ao passar para o data frame este tipo de informacao, ele ira considerar apenas as informacoes que forem True

dados_residencial = dados[selecao]
```


```python
dados_residencial
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
      <th>32953</th>
      <td>Apartamento</td>
      <td>Méier</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>900.0</td>
      <td>490.0</td>
      <td>48.0</td>
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
  </tbody>
</table>
<p>22580 rows × 9 columns</p>
</div>




```python
# podemos reparar que os index nao estao mais na ordem correta, pulando alguns numeros.
# iremos reconstruir o indice, mas antes faremos uma comparacao com a base anterior para verificar a quantia de resultados

dados_residencial.shape[0]
```




    22580




```python
# a variavel dados contem mais resultados, pois nao foi selecionado apenas os itens que queriamos!
dados.shape[0]
```




    32960




```python
# com isso corrigimos o index
dados_residencial.index = range(dados_residencial.shape[0])
```


```python
dados_residencial
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
      <th>22575</th>
      <td>Apartamento</td>
      <td>Méier</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>900.0</td>
      <td>490.0</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>22576</th>
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
      <th>22577</th>
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
      <th>22578</th>
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
      <th>22579</th>
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
  </tbody>
</table>
<p>22580 rows × 9 columns</p>
</div>



## Exportando base de dados


```python
dados_residencial.to_csv('dados/aluguel_residencial.csv', sep = ';')
```


```python
dados_residencial_2 = pd.read_csv('dados/aluguel_residencial.csv', sep=';')
```


```python
# podemos ver que o index foi exportando como se fosse uma variavel
dados_residencial_2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
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
      <td>0</td>
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
      <td>1</td>
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
      <td>2</td>
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
      <td>3</td>
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
      <td>4</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>22575</th>
      <td>22575</td>
      <td>Apartamento</td>
      <td>Méier</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>900.0</td>
      <td>490.0</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>22576</th>
      <td>22576</td>
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
      <th>22577</th>
      <td>22577</td>
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
      <th>22578</th>
      <td>22578</td>
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
      <th>22579</th>
      <td>22579</td>
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
  </tbody>
</table>
<p>22580 rows × 10 columns</p>
</div>




```python
# entao iremos concertar isso removendo.
dados_residencial.to_csv('dados/aluguel_residencial.csv', sep = ';', index = False)
```


```python
dados_residencial_2 = pd.read_csv('dados/aluguel_residencial.csv', sep=';')
```


```python
dados_residencial_2
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
      <th>22575</th>
      <td>Apartamento</td>
      <td>Méier</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>900.0</td>
      <td>490.0</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>22576</th>
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
      <th>22577</th>
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
      <th>22578</th>
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
      <th>22579</th>
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
  </tbody>
</table>
<p>22580 rows × 9 columns</p>
</div>




```python

```
