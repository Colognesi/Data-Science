# Relatorio de analise 6

## criando novas variaveis


```python
import pandas as pd
```


```python
dados = pd.read_csv('dados/aluguel_residencial.csv', sep = ';')
dados
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
dados.to_csv('dados/aluguel_residencial.csv', sep=';', index = False)
```
