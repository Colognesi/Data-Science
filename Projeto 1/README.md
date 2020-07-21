# Resumo dos relatórios
Nesse readme, irei postar o todos os dados extraídos e a progressão feita nessa analise.</br> 
Também irei adicionar links para os relatorios separados, para caso queira verificar um relatorio em particular.

## Relatorio de analise 1
Usado para descobrir os itens presentes na base de dados fornecida.

Link para a área: [Relatório de analise 1](#fast_travel1)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Base%20de%20Dados%20(relatorio1).md" target="_blank"> Relatorio de analise 1 separado </a>

## Relatorio de analise 2
Realizado para isolar as categorias de imoveis, assim não veremos duplicatas.

Link para a área: [Relatório de analise 2](#fast_travel2)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Tipos%20de%20Imoveis%20(relatorio2).md" target="_blank"> Relatorio de analise 2 separado </a>


## Relatorio de analise 3
Relatorio realizado para isolar os tipos de imoveis apenas para imoveis residenciais.</br>
Concluindo com a exportação do arquivo para outros relatorios.</br>

Link para a área: [Relatório de analise 3](#fast_travel3)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Im%C3%B3veis%20Residenciais%20(relatorio3).md" target="_blank">Relatório de analise 3 separado </a>


## Relatorio de analise 4
Relatorio realizado com o objetivo de cumprir 4 criterios para seleção de itens:

selecionar imoveis classificados por Apartamento</br>
selecionar imoveis classificados como casa, casa de condominio e casa de vila</br>
selecionar imoveis com area entre 60 e 100 m² incluindo os limites</br>
selecionar imoveis que tenham pelo menos 4 quartos e aluguel menor que 2000</br>

Link para a área: [Relatório de analise 4](#fast_travel4)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Selecoes%20e%20Frequencias%20(relatorio4).md" tartet="_blank">Relatório de analise 4 separado </a>

## Relatorio de analise 5
Relatorio para iniciar a tratativa de dados faltantes. Removendo alguns registros e adicionando valores a outros

Link para a área: [Relatório de analise 5](#fast_travel5)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Tratamento%20de%20dados%20faltantes(relatorio5).md" target="_blank">Relatório de analise 5 separado </a>

## Relatorio de analise 6
Criado para adicionar novas variaveis(colunas) e também removendo algumas.

Link para a área: [Relatório de analise 6](#fast_travel6)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/criando%20novas%20variaveis(relatorio6).md" target="_blank">Relatório de analise 6 separado</a>

## Relatorio de analise 7
Relatorio realizado para realizar uma analise descritiva dos dados, como frequencias, medias de valores e representações graficas de locais</br>
Link para a área: [Relatório de analise 7](#fast_travel7)</br>
Caso queira verificar este relatório separadamente, o link é este: <a href="https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Relatorios%20MD%20separados/Criando%20Agrupamentos.md">Relatório de analise 6 separado</a></br>

Também realizei uma verificação nas maiores frequencias, separei os bairros com maior quantidades de entradas e realizei uma demonstração gráfica de seus valores.</br>
O link para esta área: [Relatorio com base na frequencia](#fast_travel71)


</br></br></br></br></br></br></br></br></br></br></br></br></br>


# <a name = "fast_travel1"/> Relatorio analise 1

Neste relatorio, foi feita uma analise exploratoria para descobrir o que continha estes dados.</br>
Contem uma base com informações de imóveis e bairros do rio de janeiro.</br>

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
# Verificando info para melhor visualizar as colunas e tipos de objetos
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
    
# <a name="fast_travel2"/> Relatorio de analise 2


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


# <a name="fast_travel3"/> Relatorio de analise 3

Neste notebook nosso objetivo é isolar apenas imoveis residenciais e exportar o arquivo contendo as informacoes.

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

# <a name = "fast_travel4"/> Relatorio de analise 4

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
    
# <a name="fast_travel5"/> Relatorio de analise 5

## tratamento de dados faltantes


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep=';')
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
  </tbody>
</table>
</div>




```python
# vamos remover dados Nan, existe a funcao isnull para encontrar esses carinhas
dados.isnull()
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
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
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
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>22576</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>22577</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>22578</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>22579</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>22580 rows × 9 columns</p>
</div>




```python
# tambem temos o notnull
dados.notnull()
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
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
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
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>22576</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>22577</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>22578</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>22579</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>22580 rows × 9 columns</p>
</div>




```python
dados.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 22580 entries, 0 to 22579
    Data columns (total 9 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   Tipo        22580 non-null  object 
     1   Bairro      22580 non-null  object 
     2   Quartos     22580 non-null  int64  
     3   Vagas       22580 non-null  int64  
     4   Suites      22580 non-null  int64  
     5   Area        22580 non-null  int64  
     6   Valor       22571 non-null  float64
     7   Condominio  20765 non-null  float64
     8   IPTU        15795 non-null  float64
    dtypes: float64(3), int64(4), object(2)
    memory usage: 1.6+ MB
    


```python
dados['Valor'].isnull()
```




    0        False
    1        False
    2        False
    3        False
    4        False
             ...  
    22575    False
    22576    False
    22577    False
    22578    False
    22579    False
    Name: Valor, Length: 22580, dtype: bool




```python
dados[dados['Valor'].isnull()]
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
      <th>58</th>
      <td>Apartamento</td>
      <td>Barra da Tijuca</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>70</td>
      <td>NaN</td>
      <td>970.0</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>1492</th>
      <td>Apartamento</td>
      <td>Leme</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>75</td>
      <td>NaN</td>
      <td>878.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1683</th>
      <td>Casa</td>
      <td>Campo Grande</td>
      <td>3</td>
      <td>4</td>
      <td>3</td>
      <td>363</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2012</th>
      <td>Apartamento</td>
      <td>Botafogo</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>95</td>
      <td>NaN</td>
      <td>1010.0</td>
      <td>170.0</td>
    </tr>
    <tr>
      <th>2034</th>
      <td>Apartamento</td>
      <td>Copacabana</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>72</td>
      <td>NaN</td>
      <td>850.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4941</th>
      <td>Casa</td>
      <td>Campo Grande</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>100</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8568</th>
      <td>Apartamento</td>
      <td>Leme</td>
      <td>2</td>
      <td>0</td>
      <td>1</td>
      <td>75</td>
      <td>NaN</td>
      <td>878.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8947</th>
      <td>Apartamento</td>
      <td>Glória</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>135</td>
      <td>NaN</td>
      <td>910.0</td>
      <td>228.0</td>
    </tr>
    <tr>
      <th>9149</th>
      <td>Apartamento</td>
      <td>Gávea</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>105</td>
      <td>NaN</td>
      <td>880.0</td>
      <td>221.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# podemos usar o dropna para remover os dados nan
a = dados.shape[0]
dados.dropna(subset = ['Valor'], inplace = True)
b = dados.shape[0]
a - b
```




    9




```python
# removemos os valores nan, agora iremos remover os condominios nan
dados[dados['Valor'].isnull()]
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
  </tbody>
</table>
</div>




```python
# sabemos que existem 1813 codominios nulos
dados[dados['Condominio'].isnull()].shape[0]
```




    1813




```python
selecao = (dados['Tipo'] == 'Apartamento') & (dados['Condominio'].isnull())
a = dados.shape[0]
dados = dados[~selecao] # para inverter a series boleana, usamos o ~, o que é true vira false e o que e false vira true
b = dados.shape[0]
a - b
```




    745




```python
dados[dados['Condominio'].isnull()].shape[0]
```




    1068




```python
# para nao jogarmos o restante dos valores fora, faremos o seguinte:
dados = dados.fillna({'Condominio':0, 'IPTU':0})
```


```python
dados[dados['Condominio'].isnull()].shape[0]
```




    0




```python
dados[dados['IPTU'].isnull()].shape[0]
```




    0




```python
dados.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 21826 entries, 0 to 22579
    Data columns (total 9 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   Tipo        21826 non-null  object 
     1   Bairro      21826 non-null  object 
     2   Quartos     21826 non-null  int64  
     3   Vagas       21826 non-null  int64  
     4   Suites      21826 non-null  int64  
     5   Area        21826 non-null  int64  
     6   Valor       21826 non-null  float64
     7   Condominio  21826 non-null  float64
     8   IPTU        21826 non-null  float64
    dtypes: float64(3), int64(4), object(2)
    memory usage: 1.7+ MB
    


```python
dados.to_csv('dados/aluguel_residencial.csv', sep=';', index = False)
```
# <a name="fast_travel6"/> Relatorio de analise 6

## criando novas variaveis


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep = ';')
dados
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
      <td>0.0</td>
      <td>0.0</td>
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
      <td>0.0</td>
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
      <th>21821</th>
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
      <th>21822</th>
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
      <th>21823</th>
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
      <th>21824</th>
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
      <th>21825</th>
      <td>Apartamento</td>
      <td>Leblon</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>3000.0</td>
      <td>760.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>21826 rows × 9 columns</p>
</div>




```python
# Uma variável para abrigar o valor bruto do aluguel
dados['Valor Bruto'] = dados['Valor'] + dados['Condominio'] + dados['IPTU']
dados
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
      <th>Valor Bruto</th>
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
      <td>2260.0</td>
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
      <td>7000.0</td>
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
      <td>1210.0</td>
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
      <td>1030.0</td>
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
      <td>1618.0</td>
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
      <th>21821</th>
      <td>Apartamento</td>
      <td>Méier</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>900.0</td>
      <td>490.0</td>
      <td>48.0</td>
      <td>1438.0</td>
    </tr>
    <tr>
      <th>21822</th>
      <td>Quitinete</td>
      <td>Centro</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>27</td>
      <td>800.0</td>
      <td>350.0</td>
      <td>25.0</td>
      <td>1175.0</td>
    </tr>
    <tr>
      <th>21823</th>
      <td>Apartamento</td>
      <td>Jacarepaguá</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>78</td>
      <td>1800.0</td>
      <td>800.0</td>
      <td>40.0</td>
      <td>2640.0</td>
    </tr>
    <tr>
      <th>21824</th>
      <td>Apartamento</td>
      <td>São Francisco Xavier</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>48</td>
      <td>1400.0</td>
      <td>509.0</td>
      <td>37.0</td>
      <td>1946.0</td>
    </tr>
    <tr>
      <th>21825</th>
      <td>Apartamento</td>
      <td>Leblon</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>70</td>
      <td>3000.0</td>
      <td>760.0</td>
      <td>0.0</td>
      <td>3760.0</td>
    </tr>
  </tbody>
</table>
<p>21826 rows × 10 columns</p>
</div>




```python
# Armazena o valor com base no metrô quadrado de um imóvel
dados['Valor m2'] = dados['Valor'] / dados['Area']
dados['Valor m2'] = dados['Valor m2'].round(2)
dados['Valor Bruto m2'] = (dados['Valor Bruto']/dados['Area']).round(2)
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
      <th>Valor Bruto</th>
      <th>Valor m2</th>
      <th>Valor Bruto m2</th>
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
      <td>2260.0</td>
      <td>42.50</td>
      <td>56.50</td>
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
      <td>7000.0</td>
      <td>70.00</td>
      <td>70.00</td>
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
      <td>1210.0</td>
      <td>53.33</td>
      <td>80.67</td>
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
      <td>1030.0</td>
      <td>16.67</td>
      <td>21.46</td>
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
      <td>1618.0</td>
      <td>26.00</td>
      <td>32.36</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Casa de Condomínio</td>
      <td>Barra da Tijuca</td>
      <td>5</td>
      <td>4</td>
      <td>5</td>
      <td>750</td>
      <td>22000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>22000.0</td>
      <td>29.33</td>
      <td>29.33</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Casa de Condomínio</td>
      <td>Ramos</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>65</td>
      <td>1000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1000.0</td>
      <td>15.38</td>
      <td>15.38</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Apartamento</td>
      <td>Grajaú</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1500.0</td>
      <td>642.0</td>
      <td>74.0</td>
      <td>2216.0</td>
      <td>21.43</td>
      <td>31.66</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Apartamento</td>
      <td>Lins de Vasconcelos</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>90</td>
      <td>1500.0</td>
      <td>455.0</td>
      <td>14.0</td>
      <td>1969.0</td>
      <td>16.67</td>
      <td>21.88</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Apartamento</td>
      <td>Copacabana</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>40</td>
      <td>2000.0</td>
      <td>561.0</td>
      <td>50.0</td>
      <td>2611.0</td>
      <td>50.00</td>
      <td>65.28</td>
    </tr>
  </tbody>
</table>
</div>




```python
# variável de tipo que agregue casas e apartamentos
casa = ['Casa','Casa de Condomínio', 'Casa de Vila']
dados['Tipo Agregado'] = dados['Tipo'].apply(lambda x: 'Casa' if x in casa else 'Apartamento')
# apply permite que apliquemos uma funcao a cada linha ou registro de nosso dataframe
# lambda e uma funcao na qual pode-se adicionar qualquer numero de argumentos, porem deve ter apenas uma expressao
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
      <th>Valor Bruto</th>
      <th>Valor m2</th>
      <th>Valor Bruto m2</th>
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
      <td>2260.0</td>
      <td>42.50</td>
      <td>56.50</td>
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
      <td>7000.0</td>
      <td>70.00</td>
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
      <td>1210.0</td>
      <td>53.33</td>
      <td>80.67</td>
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
      <td>1030.0</td>
      <td>16.67</td>
      <td>21.46</td>
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
      <td>1618.0</td>
      <td>26.00</td>
      <td>32.36</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Casa de Condomínio</td>
      <td>Barra da Tijuca</td>
      <td>5</td>
      <td>4</td>
      <td>5</td>
      <td>750</td>
      <td>22000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>22000.0</td>
      <td>29.33</td>
      <td>29.33</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Casa de Condomínio</td>
      <td>Ramos</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>65</td>
      <td>1000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1000.0</td>
      <td>15.38</td>
      <td>15.38</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Apartamento</td>
      <td>Grajaú</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1500.0</td>
      <td>642.0</td>
      <td>74.0</td>
      <td>2216.0</td>
      <td>21.43</td>
      <td>31.66</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Apartamento</td>
      <td>Lins de Vasconcelos</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>90</td>
      <td>1500.0</td>
      <td>455.0</td>
      <td>14.0</td>
      <td>1969.0</td>
      <td>16.67</td>
      <td>21.88</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Apartamento</td>
      <td>Copacabana</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>40</td>
      <td>2000.0</td>
      <td>561.0</td>
      <td>50.0</td>
      <td>2611.0</td>
      <td>50.00</td>
      <td>65.28</td>
      <td>Apartamento</td>
    </tr>
  </tbody>
</table>
</div>



## Excluindo variaveis


```python
dados_aux = pd.DataFrame(dados[['Tipo Agregado', 'Valor m2', 'Valor Bruto', 'Valor Bruto m2']])
dados_aux.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo Agregado</th>
      <th>Valor m2</th>
      <th>Valor Bruto</th>
      <th>Valor Bruto m2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Apartamento</td>
      <td>42.50</td>
      <td>2260.0</td>
      <td>56.50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
      <td>70.00</td>
      <td>7000.0</td>
      <td>70.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Apartamento</td>
      <td>53.33</td>
      <td>1210.0</td>
      <td>80.67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
      <td>16.67</td>
      <td>1030.0</td>
      <td>21.46</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Apartamento</td>
      <td>26.00</td>
      <td>1618.0</td>
      <td>32.36</td>
    </tr>
  </tbody>
</table>
</div>




```python
del dados_aux['Valor Bruto'] 
dados_aux
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo Agregado</th>
      <th>Valor m2</th>
      <th>Valor Bruto m2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Apartamento</td>
      <td>42.50</td>
      <td>56.50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
      <td>70.00</td>
      <td>70.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Apartamento</td>
      <td>53.33</td>
      <td>80.67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
      <td>16.67</td>
      <td>21.46</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Apartamento</td>
      <td>26.00</td>
      <td>32.36</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21821</th>
      <td>Apartamento</td>
      <td>12.86</td>
      <td>20.54</td>
    </tr>
    <tr>
      <th>21822</th>
      <td>Apartamento</td>
      <td>29.63</td>
      <td>43.52</td>
    </tr>
    <tr>
      <th>21823</th>
      <td>Apartamento</td>
      <td>23.08</td>
      <td>33.85</td>
    </tr>
    <tr>
      <th>21824</th>
      <td>Apartamento</td>
      <td>29.17</td>
      <td>40.54</td>
    </tr>
    <tr>
      <th>21825</th>
      <td>Apartamento</td>
      <td>42.86</td>
      <td>53.71</td>
    </tr>
  </tbody>
</table>
<p>21826 rows × 3 columns</p>
</div>




```python
dados_aux.pop('Valor Bruto m2')
dados_aux
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tipo Agregado</th>
      <th>Valor m2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Apartamento</td>
      <td>42.50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Casa</td>
      <td>70.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Apartamento</td>
      <td>53.33</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apartamento</td>
      <td>16.67</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Apartamento</td>
      <td>26.00</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21821</th>
      <td>Apartamento</td>
      <td>12.86</td>
    </tr>
    <tr>
      <th>21822</th>
      <td>Apartamento</td>
      <td>29.63</td>
    </tr>
    <tr>
      <th>21823</th>
      <td>Apartamento</td>
      <td>23.08</td>
    </tr>
    <tr>
      <th>21824</th>
      <td>Apartamento</td>
      <td>29.17</td>
    </tr>
    <tr>
      <th>21825</th>
      <td>Apartamento</td>
      <td>42.86</td>
    </tr>
  </tbody>
</table>
<p>21826 rows × 2 columns</p>
</div>




```python
# axis 1 = coluna, 0 = linha
dados.drop(['Valor Bruto', 'Valor Bruto m2'], axis = 1, inplace = True)
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
    <tr>
      <th>5</th>
      <td>Casa de Condomínio</td>
      <td>Barra da Tijuca</td>
      <td>5</td>
      <td>4</td>
      <td>5</td>
      <td>750</td>
      <td>22000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>29.33</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Casa de Condomínio</td>
      <td>Ramos</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>65</td>
      <td>1000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>15.38</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Apartamento</td>
      <td>Grajaú</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1500.0</td>
      <td>642.0</td>
      <td>74.0</td>
      <td>21.43</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Apartamento</td>
      <td>Lins de Vasconcelos</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>90</td>
      <td>1500.0</td>
      <td>455.0</td>
      <td>14.0</td>
      <td>16.67</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Apartamento</td>
      <td>Copacabana</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>40</td>
      <td>2000.0</td>
      <td>561.0</td>
      <td>50.0</td>
      <td>50.00</td>
      <td>Apartamento</td>
    </tr>
  </tbody>
</table>
</div>

```python
dados.to_csv('dados/aluguel_residencial.csv', sep=';', index = False)
```

# <a name = 'fast_travel7'/> Relatório de analise 7

## Criando agrupamentos


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep = ';')
```


```python
dados.Bairro.unique()
```




    array(['Copacabana', 'Jardim Botânico', 'Centro', 'Higienópolis',
           'Cachambi', 'Barra da Tijuca', 'Ramos', 'Grajaú',
           'Lins de Vasconcelos', 'Taquara', 'Freguesia (Jacarepaguá)',
           'Tijuca', 'Olaria', 'Ipanema', 'Campo Grande', 'Botafogo',
           'Recreio dos Bandeirantes', 'Leblon', 'Jardim Oceânico', 'Humaitá',
           'Península', 'Méier', 'Vargem Pequena', 'Maracanã', 'Jacarepaguá',
           'São Conrado', 'Vila Valqueire', 'Gávea', 'Cosme Velho',
           'Bonsucesso', 'Todos os Santos', 'Laranjeiras', 'Itanhangá',
           'Flamengo', 'Piedade', 'Lagoa', 'Catete', 'Jardim Carioca',
           'Benfica', 'Glória', 'Praça Seca', 'Vila Isabel', 'Engenho Novo',
           'Engenho de Dentro', 'Pilares', 'Água Santa', 'São Cristóvão',
           'Ilha do Governador', 'Jardim Sulacap', 'Oswaldo Cruz',
           'Vila da Penha', 'Anil', 'Vargem Grande', 'Tanque', 'Vaz Lobo',
           'Madureira', 'São Francisco Xavier', 'Pechincha', 'Leme', 'Irajá',
           'Quintino Bocaiúva', 'Urca', 'Penha', 'Gardênia Azul',
           'Rio Comprido', 'Andaraí', 'Santa Teresa', 'Inhaúma',
           'Marechal Hermes', 'Curicica', 'Santíssimo', 'Moneró', 'Camorim',
           'Cascadura', 'Praia da Bandeira', 'Saúde', 'Joá', 'Realengo',
           'Fátima', 'Inhoaíba', 'Rocha', 'Jardim Guanabara', 'Jabour',
           'Braz de Pina', 'Praça da Bandeira', 'Vila Kosmos', 'Vista Alegre',
           'Encantado', 'Campinho', 'Guaratiba', 'Riachuelo', 'Bangu', 'Lapa',
           'Catumbi', 'Penha Circular', 'Abolição', 'Tomás Coelho', 'Colégio',
           'Pavuna', 'Santa Cruz', 'Alto da Boa Vista', 'Cidade Nova',
           'Bento Ribeiro', 'Estácio', 'Jardim América', 'Cordovil', 'Caju',
           'Pedra de Guaratiba', 'Padre Miguel', 'Paciência', 'Del Castilho',
           'Arpoador', 'Sampaio', 'Anchieta', 'Icaraí', 'Senador Vasconcelos',
           'Rocha Miranda', 'Gamboa', 'Maria da Graça', 'Barra de Guaratiba',
           'Vicente de Carvalho', 'Paquetá', 'Largo do Machado',
           'Parada de Lucas', 'Freguesia (Ilha do Governador)', 'Portuguesa',
           'Guadalupe', 'Parque Anchieta', 'Turiaçu', 'Pitangueiras',
           'Vila Militar', 'Vidigal', 'Senador Camará', 'Usina',
           'Vigário Geral', 'Cosmos', 'Jacaré', 'Cocotá', 'Honório Gurgel',
           'Engenho da Rainha', 'Cachamorra', 'Zumbi', 'Tauá', 'Santo Cristo',
           'Ribeira', 'Magalhães Bastos', 'Cacuia', 'Bancários', 'Cavalcanti',
           'Rio da Prata', 'Cidade Jardim', 'Coelho Neto'], dtype=object)




```python
dados.Bairro.value_counts()
```




    Barra da Tijuca             3863
    Copacabana                  2644
    Ipanema                     1764
    Recreio dos Bandeirantes    1649
    Leblon                      1258
                                ... 
    Cidade Jardim                  1
    Caju                           1
    Cachamorra                     1
    Senador Camará                 1
    Rio da Prata                   1
    Name: Bairro, Length: 152, dtype: int64




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
    <tr>
      <th>5</th>
      <td>Casa de Condomínio</td>
      <td>Barra da Tijuca</td>
      <td>5</td>
      <td>4</td>
      <td>5</td>
      <td>750</td>
      <td>22000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>29.33</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Casa de Condomínio</td>
      <td>Ramos</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>65</td>
      <td>1000.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>15.38</td>
      <td>Casa</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Apartamento</td>
      <td>Grajaú</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>70</td>
      <td>1500.0</td>
      <td>642.0</td>
      <td>74.0</td>
      <td>21.43</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Apartamento</td>
      <td>Lins de Vasconcelos</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>90</td>
      <td>1500.0</td>
      <td>455.0</td>
      <td>14.0</td>
      <td>16.67</td>
      <td>Apartamento</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Apartamento</td>
      <td>Copacabana</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>40</td>
      <td>2000.0</td>
      <td>561.0</td>
      <td>50.0</td>
      <td>50.00</td>
      <td>Apartamento</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados['Valor'].mean()
```




    5046.172821405663




```python
bairros = ['Barra da Tijuca', 'Copacabana', 'Ipanema', 'Leblon', 'Botafogo', 'Flamengo', 'Tijuca']
selecao = dados['Bairro'].isin(bairros)
dados = dados[selecao]
```


```python
dados.Bairro.unique()
```




    array(['Copacabana', 'Barra da Tijuca', 'Tijuca', 'Ipanema', 'Botafogo',
           'Leblon', 'Flamengo'], dtype=object)




```python
dados.Bairro.value_counts()
```




    Barra da Tijuca    3863
    Copacabana         2644
    Ipanema            1764
    Leblon             1258
    Tijuca             1100
    Botafogo            873
    Flamengo            714
    Name: Bairro, dtype: int64




```python
grupo_bairro = dados.groupby('Bairro')
```


```python
grupo_bairro.groups
```




    {'Barra da Tijuca': Int64Index([    5,    14,    16,    21,    30,    32,    35,    42,    43,
                    60,
                 ...
                 21769, 21771, 21774, 21782, 21800, 21801, 21811, 21812, 21813,
                 21820],
                dtype='int64', length=3863),
     'Botafogo': Int64Index([   23,    48,    87,    88,   111,   119,   127,   134,   196,
                   200,
                 ...
                 21471, 21487, 21499, 21529, 21653, 21660, 21666, 21715, 21746,
                 21790],
                dtype='int64', length=873),
     'Copacabana': Int64Index([    0,     9,    10,    11,    24,    25,    28,    31,    86,
                    91,
                 ...
                 21707, 21713, 21736, 21743, 21780, 21783, 21795, 21809, 21810,
                 21815],
                dtype='int64', length=2644),
     'Flamengo': Int64Index([   78,   138,   218,   284,   321,   347,   356,   361,   369,
                   393,
                 ...
                 21527, 21560, 21581, 21629, 21680, 21704, 21728, 21731, 21740,
                 21794],
                dtype='int64', length=714),
     'Ipanema': Int64Index([   19,    39,    40,    45,    52,    53,    73,    84,    92,
                   114,
                 ...
                 21718, 21722, 21730, 21739, 21744, 21745, 21754, 21788, 21796,
                 21817],
                dtype='int64', length=1764),
     'Leblon': Int64Index([   27,    59,    90,    97,   115,   133,   161,   167,   171,
                   213,
                 ...
                 21721, 21761, 21770, 21777, 21785, 21786, 21787, 21808, 21816,
                 21825],
                dtype='int64', length=1258),
     'Tijuca': Int64Index([   15,    18,    20,    80,    82,   126,   145,   149,   158,
                   164,
                 ...
                 21573, 21577, 21607, 21610, 21661, 21675, 21714, 21729, 21773,
                 21818],
                dtype='int64', length=1100)}




```python
for bairro, data in grupo_bairro:
    print('{} -> {}'.format(bairro, data['Valor'].mean()))
```

    Barra da Tijuca -> 7069.552938130986
    Botafogo -> 8791.828178694159
    Copacabana -> 4126.677004538578
    Flamengo -> 4113.526610644258
    Ipanema -> 9352.001133786847
    Leblon -> 8746.344992050874
    Tijuca -> 2043.52
    


```python
grupo_bairro[['Valor', 'Condominio']].mean().round(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Valor</th>
      <th>Condominio</th>
    </tr>
    <tr>
      <th>Bairro</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Barra da Tijuca</th>
      <td>7069.55</td>
      <td>3591.01</td>
    </tr>
    <tr>
      <th>Botafogo</th>
      <td>8791.83</td>
      <td>976.28</td>
    </tr>
    <tr>
      <th>Copacabana</th>
      <td>4126.68</td>
      <td>1148.68</td>
    </tr>
    <tr>
      <th>Flamengo</th>
      <td>4113.53</td>
      <td>1102.15</td>
    </tr>
    <tr>
      <th>Ipanema</th>
      <td>9352.00</td>
      <td>2244.44</td>
    </tr>
    <tr>
      <th>Leblon</th>
      <td>8746.34</td>
      <td>2107.18</td>
    </tr>
    <tr>
      <th>Tijuca</th>
      <td>2043.52</td>
      <td>711.69</td>
    </tr>
  </tbody>
</table>
</div>



# Estatistica Descritiva


```python
# Frequencia = Count, Mean = Media, Desvio padrao = std, valor minimo = min, primeiro quartio = 25%, mediana = 50%
# Terceiro Quartio = 75%, valor maximo = max
grupo_bairro['Valor'].describe().round(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Bairro</th>
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
      <th>Barra da Tijuca</th>
      <td>3863.0</td>
      <td>7069.55</td>
      <td>11874.15</td>
      <td>800.0</td>
      <td>2500.0</td>
      <td>4500.0</td>
      <td>8500.0</td>
      <td>600000.0</td>
    </tr>
    <tr>
      <th>Botafogo</th>
      <td>873.0</td>
      <td>8791.83</td>
      <td>152202.41</td>
      <td>700.0</td>
      <td>2200.0</td>
      <td>3000.0</td>
      <td>4350.0</td>
      <td>4500000.0</td>
    </tr>
    <tr>
      <th>Copacabana</th>
      <td>2644.0</td>
      <td>4126.68</td>
      <td>3611.41</td>
      <td>100.0</td>
      <td>2000.0</td>
      <td>3000.0</td>
      <td>4800.0</td>
      <td>35000.0</td>
    </tr>
    <tr>
      <th>Flamengo</th>
      <td>714.0</td>
      <td>4113.53</td>
      <td>3839.13</td>
      <td>800.0</td>
      <td>1900.0</td>
      <td>2900.0</td>
      <td>4975.0</td>
      <td>35000.0</td>
    </tr>
    <tr>
      <th>Ipanema</th>
      <td>1764.0</td>
      <td>9352.00</td>
      <td>8219.72</td>
      <td>1200.0</td>
      <td>4500.0</td>
      <td>7000.0</td>
      <td>11000.0</td>
      <td>90000.0</td>
    </tr>
    <tr>
      <th>Leblon</th>
      <td>1258.0</td>
      <td>8746.34</td>
      <td>7004.04</td>
      <td>100.0</td>
      <td>4500.0</td>
      <td>7000.0</td>
      <td>10500.0</td>
      <td>100000.0</td>
    </tr>
    <tr>
      <th>Tijuca</th>
      <td>1100.0</td>
      <td>2043.52</td>
      <td>1664.34</td>
      <td>750.0</td>
      <td>1500.0</td>
      <td>1800.0</td>
      <td>2300.0</td>
      <td>45000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# podemos selecionar tambem valores que nos interessam separadamente.
grupo_bairro['Valor'].aggregate(['min','max']).rename(columns = {'min':'Minimo', 'max':'Maximo'})
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Minimo</th>
      <th>Maximo</th>
    </tr>
    <tr>
      <th>Bairro</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Barra da Tijuca</th>
      <td>800.0</td>
      <td>600000.0</td>
    </tr>
    <tr>
      <th>Botafogo</th>
      <td>700.0</td>
      <td>4500000.0</td>
    </tr>
    <tr>
      <th>Copacabana</th>
      <td>100.0</td>
      <td>35000.0</td>
    </tr>
    <tr>
      <th>Flamengo</th>
      <td>800.0</td>
      <td>35000.0</td>
    </tr>
    <tr>
      <th>Ipanema</th>
      <td>1200.0</td>
      <td>90000.0</td>
    </tr>
    <tr>
      <th>Leblon</th>
      <td>100.0</td>
      <td>100000.0</td>
    </tr>
    <tr>
      <th>Tijuca</th>
      <td>750.0</td>
      <td>45000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
%matplotlib inline
import matplotlib.pyplot as plt
plt.rc('figure',figsize = (20,10))
```


```python
fig = grupo_bairro['Valor'].mean().plot.bar(color = 'blue')
fig.set_ylabel('Valor do aluguel')
fig.set_title('Valor medio do aluguel por Bairro',{'fontsize':22})
```




    Text(0.5, 1.0, 'Valor medio do aluguel por Bairro')




![png](https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Dados/output_19_1.png)


### <a name = 'fast_travel71'/> Analise de aluguel por bairro (bairros com maiores frequencias)


```python
dados2 = pd.read_csv('dados/aluguel_residencial.csv',sep=';')
bairros2 = ['Barra da Tijuca', 'Copacabana', 'Recreio dos Bandeirantes', 'Leblon']
selecao2 = dados2['Bairro'].isin(bairros2)
dados2 = dados2[selecao2]
```


```python
# sabemos que nossa importação segue correta para verificar os bairros com maiores frequencias.
dados2['Bairro'].unique()
```




    array(['Copacabana', 'Barra da Tijuca', 'Recreio dos Bandeirantes',
           'Leblon'], dtype=object)




```python
# Com isso vemos a quantia de entradas dos bairros
dados2['Bairro'].value_counts()
```




    Barra da Tijuca             3863
    Copacabana                  2644
    Recreio dos Bandeirantes    1649
    Leblon                      1258
    Name: Bairro, dtype: int64




```python
# com isso conseguimos ver a analise descritiva das residencias nos bairros mencionados.
agrupamento = dados2.groupby('Bairro')
agrupamento['Valor'].describe().round(2)
```




<div>
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Bairro</th>
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
      <th>Barra da Tijuca</th>
      <td>3863.0</td>
      <td>7069.55</td>
      <td>11874.15</td>
      <td>800.0</td>
      <td>2500.0</td>
      <td>4500.0</td>
      <td>8500.0</td>
      <td>600000.0</td>
    </tr>
    <tr>
      <th>Copacabana</th>
      <td>2644.0</td>
      <td>4126.68</td>
      <td>3611.41</td>
      <td>100.0</td>
      <td>2000.0</td>
      <td>3000.0</td>
      <td>4800.0</td>
      <td>35000.0</td>
    </tr>
    <tr>
      <th>Leblon</th>
      <td>1258.0</td>
      <td>8746.34</td>
      <td>7004.04</td>
      <td>100.0</td>
      <td>4500.0</td>
      <td>7000.0</td>
      <td>10500.0</td>
      <td>100000.0</td>
    </tr>
    <tr>
      <th>Recreio dos Bandeirantes</th>
      <td>1649.0</td>
      <td>3736.61</td>
      <td>30797.79</td>
      <td>900.0</td>
      <td>1800.0</td>
      <td>2300.0</td>
      <td>3200.0</td>
      <td>1250000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# mas nossa intenção é encontrar os alugueis mais baratos. Entao vamos fazer esta seleção
# vamos verificar a base de dados2 para alugueis menores ou iguais a 1500
alugueis = dados2['Valor'] <= 1500
alugueis.value_counts()
```




    False    8681
    True      733
    Name: Valor, dtype: int64




```python
# com os dados acima, sabemos que 733 dos resultados são verdadeiros para essa seleção
# abaixo iremos visualizar quantas entradas existem para cada tipo de valor
selecao2 = dados2['Valor'] <= 1500
n1 = dados2[selecao2]
n1.Valor.value_counts()
```




    1500.0    257
    1300.0    108
    1400.0    101
    1200.0     78
    1100.0     45
    1000.0     41
    1350.0     13
    1450.0     12
    1150.0     12
    1250.0     11
    900.0      10
    800.0       8
    950.0       8
    700.0       5
    850.0       2
    1050.0      2
    100.0       2
    1190.0      1
    910.0       1
    1280.0      1
    1080.0      1
    1290.0      1
    930.0       1
    790.0       1
    1490.0      1
    1499.0      1
    1130.0      1
    750.0       1
    1480.0      1
    1230.0      1
    1070.0      1
    1380.0      1
    1180.0      1
    1140.0      1
    1390.0      1
    Name: Valor, dtype: int64




```python
# abaixo vemos em uma forma grafica a distribuição dos valores
fig = n1['Valor'].hist()
fig.set_ylabel('Quantidade de Entradas')
fig.set_title('Valor do aluguel',{'fontsize':22})
```




    Text(0.5, 1.0, 'Valor do aluguel')




![png](https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Dados/output_27_1.png)



```python
# verificamos de forma grafica, a quantia de entradas dos valores. 
# a intencao agora é verificar quantas vezes os valores aparecem nos bairros mencionados.
res = n1['Valor'].groupby(n1.Bairro)
res.describe().round(2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Bairro</th>
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
      <th>Barra da Tijuca</th>
      <td>184.0</td>
      <td>1339.89</td>
      <td>165.87</td>
      <td>800.0</td>
      <td>1200.0</td>
      <td>1400.0</td>
      <td>1500.0</td>
      <td>1500.0</td>
    </tr>
    <tr>
      <th>Copacabana</th>
      <td>373.0</td>
      <td>1265.60</td>
      <td>211.20</td>
      <td>100.0</td>
      <td>1100.0</td>
      <td>1300.0</td>
      <td>1480.0</td>
      <td>1500.0</td>
    </tr>
    <tr>
      <th>Leblon</th>
      <td>4.0</td>
      <td>1137.50</td>
      <td>692.07</td>
      <td>100.0</td>
      <td>1112.5</td>
      <td>1475.0</td>
      <td>1500.0</td>
      <td>1500.0</td>
    </tr>
    <tr>
      <th>Recreio dos Bandeirantes</th>
      <td>172.0</td>
      <td>1409.59</td>
      <td>135.54</td>
      <td>900.0</td>
      <td>1375.0</td>
      <td>1500.0</td>
      <td>1500.0</td>
      <td>1500.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import seaborn as sns
```


```python
sns.set(style="ticks")
```


```python
res2= n1.loc[1:][['Bairro','Valor']]
res2.index = range(res2.shape[0])
```


```python
# esse eu mantive apenas porquê ficou parecendo uma pipa
sns.lineplot(data=res2 , x='Bairro',y='Valor')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1b88fb622c8>




![png](https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Dados/output_32_1.png)



```python
sns.pairplot(x_vars='Bairro', y_vars='Valor', data=res2, height=8, hue="Bairro")
```




    <seaborn.axisgrid.PairGrid at 0x1b88fbc4408>




![png](https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Dados/output_33_1.png)



```python
plt.figure(figsize=(12, 6))
for i in res2['Bairro'].unique():
    sns.distplot(res2[res2['Bairro'] == i]['Valor'], hist=False, rug=False, label = i)
plt.plot()
```


![png](https://github.com/Colognesi/Data-Science/blob/master/Projeto%201/Dados/output_34_1.png)



```python
# A nossa intenção, era demonstrar de forma gráfica a distribuição dos valores, 
# com o gráfico acima, conseguimos verificar isso.
# Os valores mostram até 2000, porque o valor que selecionamos é de menor ou igual a 1500, 
# então ele nos deu uma linha que ia caindo apos o parametro que colocamos.
```

