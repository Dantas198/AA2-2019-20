# AA 2019-2020

## Índice


## Grupo
- Marco Dantas, A81736
- Luís Macedo, A80494

## Datasets

### Publico

- [GitHub - Dados mundiais sobre Covid-19](https://github.com/owid/covid-19-data)
- [GitHub - Dados sobre Covid-19 em Portugal](https://github.com/dssg-pt/covid19pt-data)

### Customizados

- [Dados com os input relevantes](https://github.com/FallenFoil/AA2-2019-20/blob/master/data/modified_dataset.csv)
- [Dados com confirmados e óbitos de Portugal e outros países parecidos](https://github.com/FallenFoil/AA2-2019-20/blob/master/data/portugal_group_dataset.csv)

## Dependências

- numpy
- pandas
- matplotlib
- intertools
- sklearn
- seaborn
- math
- keras
- tensorflow

## Organização do repositório

- **data**: ficheiros csv gerados;
- **AA2-Covid-19-Parte I**:
  - Exploração dos dados
  - Otimização dos atributos de *input*;
- **AA2-Covid-19-Parte II**:
  - Uso de métodos tradicionais de *Machine Learning*;
- **AA2-Covid-19-Parte III**:
  - Agrupamento de dados de países semelhantes a Portugal;
- **AA2-Covid-19-Parte IV**:
  - Uso de *Deep Learning*(*LSTM*);

## Objetivos

Neste projeto pretende-se:
- prever o numero de pessoas infetadas com o Covid-19;
- prever o numero de fatalidades devido ao Covid-19;
- Identificar fatores relevantes para as previsões anteriores.

## Sumario

Inicialmente é feito uma analise ao dataset com a serie temporal da expansão do Covid-19 pelo mundo, como por exemplo, comparar a progressão na China com a Nigeria.

![China_VS_Nigeria](images/china_vs_nigeria.png)

De seguida, o foco passa a ser Portugal. Com a ajuda do dataset referido acima, são construídos gráficos e tabelas que demonstram a situação atual.

![portugal](images/portugal.png)

Por forma a tornar a previsão mais simples, foi preciso reduzir o número de features relevantes. Logo à partida percebe-se que o numero de confirmados é importante. Foi também executado um isolamento no dataset, separando por faixas etárias (Jovens, Idade Media e Terceira Idade), tirando conclusões com o dados obtidos.

De seguida, é preparado e analisado os dados sobre os sintomas, concluindo que a tosse é o maior sintoma.

![Sintomas](images/sintomas.png)

Para melhor previsões, foi introduzido o conceito de **lags**, sendo usado logo de seguida.

Para a primeira previsão foi usado um regressão linear, obtendo as seguintes previsões:

![regressao_linear](images/regressao_linear.png)

## Pequena demonstração de cada Dataset

### GitHub - Dados mundiais sobre Covid-19

| iso_code | continent | location | date       | total_cases | new_cases | total_deaths | new_deaths | total_cases_per_million | new_cases_per_million | ... |
|----------|-----------|----------|------------|-------------|-----------|--------------|------------|-------------------------|-----------------------|-----|
| PRT      | Europe    | Portugal | 2020-06-21 | 38841.0     | 377.0     | 1528.0       | 1.0        | 3809.171                | 36.973                | ... |
| PRT      | Europe    | Portugal | 2020-06-22 | 39133.0     | 292.0     | 1530.0       | 2.0        | 3837.808                | 28.637                | ... |
| PRT      | Europe    | Portugal | 2020-06-23 | 39392.0     | 259.0     | 1534.0       | 4.0        | 3863.208                | 25.4                  | ... |
| PRT      | Europe    | Portugal | 2020-06-24 | 39737.0     | 345.0     | 1540.0       | 6.0        | 3897.042                | 33.834                | ... |

### GitHub - Dados mundiais sobre Covid-19

| data       | data_dados       | confirmados | confirmados_arsnorte | confirmados_arscentro | confirmados_arslvt | confirmados_arsalentejo | confirmados_arsalgarve | ... |
|------------|------------------|-------------|----------------------|-----------------------|--------------------|-------------------------|------------------------|-----|
| 20-06-2020 | 20-06-2020 00:00 | 38841       | 17242                | 3966                  | 16537              | 363                     | 499                    | ... |
| 21-06-2020 | 21-06-2020 00:00 | 39133       | 17249                | 3991                  | 16762              | 374                     | 521                    | ... |
| 22-06-2020 | 22-06-2020 00:00 | 39392       | 17320                | 4005                  | 16926              | 376                     | 529                    | ... |
| 23-06-2020 | 23-06-2020 00:00 | 39737       | 17329                | 4014                  | 17225              | 397                     | 536                    | ... |
| 24-06-2020 | 24-06-2020 00:00 | 40104       | 17339                | 4042                  | 17527              | 406                     | 552                    | ... |


### portugal_group_dataset.csv

|   | location | new_cases_per_million | new_deaths_per_million |
|---|----------|-----------------------|------------------------|
| 0 | Austria  | 1.3319999999999999    | 0.0                    |
| 1 | Austria  | 3.6639999999999997    | 0.0                    |
| 2 | Austria  | 2.7760000000000002    | 0.0                    |
| 3 | Austria  | 0.33299999999999996   | 0.0                    |

### modified_dataset.csv

|     | confirmados_novos | internados | internados_uci | lab    | vigilancia | obitos_novos | suspeitos_novos | lab_lag_1 | lab_lag_2 | ... |
|-----|-------------------|------------|----------------|--------|------------|--------------|-----------------|-----------|-----------|-----|
| 112 | 259               | 424.0      | 72.0           | 1782.0 | 30956.0    | 4.0          | 1172.0          | 1826.0    | 1771.0    | ... |
| 113 | 345               | 441.0      | 72.0           | 1759.0 | 30248.0    | 6.0          | 2472.0          | 1782.0    | 1826.0    | ... |