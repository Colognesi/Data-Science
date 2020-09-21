# Relatório de analise 7

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




![png](output_19_1.png)


### Analise de aluguel por bairro (bairros com maiores frequencias)


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




![png](output_27_1.png)



```python
# verificamos de forma grafica, a quantia de entradas dos valores. 
# a intencao agora é verificar quantas vezes os valores aparecem nos bairros mencionados.
res = n1['Valor'].groupby(n1.Bairro)
res.describe().round(2)
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




![png](output_32_1.png)



```python
sns.pairplot(x_vars='Bairro', y_vars='Valor', data=res2, height=8, hue="Bairro")
```




    <seaborn.axisgrid.PairGrid at 0x1b88fbc4408>




![png](output_33_1.png)



```python
plt.figure(figsize=(12, 6))
for i in res2['Bairro'].unique():
    sns.distplot(res2[res2['Bairro'] == i]['Valor'], hist=False, rug=False, label = i)
plt.plot()
```




    []




![png](output_34_1.png)



```python

```
