# Relatorio de analise 2


```python
# Neste relatorio, nosso objetivo é isolar as categorias de imoveis
```

## Tipos de imoveis


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel.csv', sep = ';')
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




```python
dados['Tipo']
```




    0                      Quitinete
    1                           Casa
    2        Conjunto Comercial/Sala
    3                    Apartamento
    4                    Apartamento
                      ...           
    32955                  Quitinete
    32956                Apartamento
    32957                Apartamento
    32958                Apartamento
    32959    Conjunto Comercial/Sala
    Name: Tipo, Length: 32960, dtype: object




```python
tipo_de_imovel = dados['Tipo']
type(tipo_de_imovel)
```




    pandas.core.series.Series




```python
# drop_duplicates utilizado para isolar tipos de imoveis, nao mostrando duplicatas
tipo_de_imovel.drop_duplicates()
```




    0                          Quitinete
    1                               Casa
    2            Conjunto Comercial/Sala
    3                        Apartamento
    7                 Casa de Condomínio
    16                    Prédio Inteiro
    17                              Flat
    29                        Loja/Salão
    80           Galpão/Depósito/Armazém
    83                    Casa Comercial
    117                     Casa de Vila
    159                   Terreno Padrão
    207                      Box/Garagem
    347                             Loft
    589      Loja Shopping/ Ct Comercial
    2157                         Chácara
    3354           Loteamento/Condomínio
    4379                           Sítio
    4721                   Pousada/Chalé
    6983                          Studio
    9687                           Hotel
    23614                      Indústria
    Name: Tipo, dtype: object




```python
# Para dropar os tipos de imoveis de forma fixa, deve-se usar um argumento dentro da função drop_duplicates
# exemplo abaixo que a variavel em si, nao obteve nenhuma alteração
tipo_de_imovel
```




    0                      Quitinete
    1                           Casa
    2        Conjunto Comercial/Sala
    3                    Apartamento
    4                    Apartamento
                      ...           
    32955                  Quitinete
    32956                Apartamento
    32957                Apartamento
    32958                Apartamento
    32959    Conjunto Comercial/Sala
    Name: Tipo, Length: 32960, dtype: object




```python
# O argumento se chama: inplace e vem marcado como false na função drop_duplicate.
# abaixo o metodo de como fazer esta remoção
tipo_de_imovel.drop_duplicates(inplace = True)
```


```python
tipo_de_imovel
```




    0                          Quitinete
    1                               Casa
    2            Conjunto Comercial/Sala
    3                        Apartamento
    7                 Casa de Condomínio
    16                    Prédio Inteiro
    17                              Flat
    29                        Loja/Salão
    80           Galpão/Depósito/Armazém
    83                    Casa Comercial
    117                     Casa de Vila
    159                   Terreno Padrão
    207                      Box/Garagem
    347                             Loft
    589      Loja Shopping/ Ct Comercial
    2157                         Chácara
    3354           Loteamento/Condomínio
    4379                           Sítio
    4721                   Pousada/Chalé
    6983                          Studio
    9687                           Hotel
    23614                      Indústria
    Name: Tipo, dtype: object



## Organizando a visualizacao


```python
# transformamos a variavel tipo_de_imovel em um DataFrame, assim poderemos visualiza-la um pouco melhor
tipo_de_imovel = pd.DataFrame(tipo_de_imovel)
```


```python
tipo_de_imovel
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Quitinete</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Conjunto Comercial/Sala</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Casa de Condomínio</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Prédio Inteiro</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Flat</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Loja/Salão</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Galpão/Depósito/Armazém</td>
    </tr>
    <tr>
      <th>83</th>
      <td>Casa Comercial</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Casa de Vila</td>
    </tr>
    <tr>
      <th>159</th>
      <td>Terreno Padrão</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Box/Garagem</td>
    </tr>
    <tr>
      <th>347</th>
      <td>Loft</td>
    </tr>
    <tr>
      <th>589</th>
      <td>Loja Shopping/ Ct Comercial</td>
    </tr>
    <tr>
      <th>2157</th>
      <td>Chácara</td>
    </tr>
    <tr>
      <th>3354</th>
      <td>Loteamento/Condomínio</td>
    </tr>
    <tr>
      <th>4379</th>
      <td>Sítio</td>
    </tr>
    <tr>
      <th>4721</th>
      <td>Pousada/Chalé</td>
    </tr>
    <tr>
      <th>6983</th>
      <td>Studio</td>
    </tr>
    <tr>
      <th>9687</th>
      <td>Hotel</td>
    </tr>
    <tr>
      <th>23614</th>
      <td>Indústria</td>
    </tr>
  </tbody>
</table>
</div>




```python
# O index dos tipos parou de fazer sentido, pois removemos as duplicatas. Entao vamos alterá-lo
# com a função index, podemos visualizar quantas entradas temos para essa visualizacao.
tipo_de_imovel.index
```




    Int64Index([    0,     1,     2,     3,     7,    16,    17,    29,    80,
                   83,   117,   159,   207,   347,   589,  2157,  3354,  4379,
                 4721,  6983,  9687, 23614],
               dtype='int64')




```python
# Com a funcao shape, selecionamos o indice 0 do nosso DataFrame (que sao os numeros sem sentido ate entao)
# Ele irá mostrar para nos a quantidade de index'es registrados no nosso dataframe atual.
tipo_de_imovel.shape[0]
```




    22




```python
# o range cria para nos uma serie de index'es de 0 a 22. é isso que queremos adicionar a nossa variavel tipo_de_imovel 
# para mostrar isoladamente todas as categorias de imoveis e indexados corretamente.
range(tipo_de_imovel.shape[0])
```




    range(0, 22)




```python
# lembrando que o index começa no 0 e vai ate o numero selecionado (descobrimos o numero selecionado no shape)
# e tambem nao mostra o ultimo item (que seria no caso 22).
for i in range(tipo_de_imovel.shape[0]):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    


```python
# para adicionarmos o range acima, podemos fazer assim:
tipo_de_imovel.index = range(tipo_de_imovel.shape[0])
```


```python
tipo_de_imovel
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Quitinete</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Conjunto Comercial/Sala</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Casa de Condomínio</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Prédio Inteiro</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Flat</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Loja/Salão</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Galpão/Depósito/Armazém</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Casa Comercial</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Casa de Vila</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Terreno Padrão</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Box/Garagem</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Loft</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Loja Shopping/ Ct Comercial</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Chácara</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Loteamento/Condomínio</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Sítio</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Pousada/Chalé</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Studio</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Hotel</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Indústria</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Agora vamos nomear a nossa coluna de index'es.
tipo_de_imovel.columns.name = 'Id'
```


```python
tipo_de_imovel
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Id</th>
      <th>Tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Quitinete</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Conjunto Comercial/Sala</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Casa de Condomínio</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Prédio Inteiro</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Flat</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Loja/Salão</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Galpão/Depósito/Armazém</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Casa Comercial</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Casa de Vila</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Terreno Padrão</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Box/Garagem</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Loft</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Loja Shopping/ Ct Comercial</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Chácara</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Loteamento/Condomínio</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Sítio</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Pousada/Chalé</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Studio</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Hotel</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Indústria</td>
    </tr>
  </tbody>
</table>
</div>




```python
tipo_de_imovel.rename(columns={'Tipo': 'Categoria'}, inplace = True)
```


```python
tipo_de_imovel
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Id</th>
      <th>Categoria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Quitinete</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Conjunto Comercial/Sala</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Casa de Condomínio</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Prédio Inteiro</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Flat</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Loja/Salão</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Galpão/Depósito/Armazém</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Casa Comercial</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Casa de Vila</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Terreno Padrão</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Box/Garagem</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Loft</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Loja Shopping/ Ct Comercial</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Chácara</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Loteamento/Condomínio</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Sítio</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Pousada/Chalé</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Studio</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Hotel</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Indústria</td>
    </tr>
  </tbody>
</table>
</div>


