# Dados: imunização de covid-19 no Brasil

Este repositório centraliza os dados coletados e processados pelo projeto [clean-data-covid-vaccination-brazil](https://github.com/raphsilva/clean-data-covid-vaccination-brazil). 
O diretório `data` está organizado em subdiretórios que contêm dados relativos às unidades federativas. 
Dentro de cada subdiretório, há as seguintes seções:

* `_info`: Informações gerais sobre os dados coletados. 
* `consistent`: Dados agregados contemplando os microdados para os quais não foram detectadas inconsistências de informações. 
* `inconsistent`: Dados agregados contemplando os microdados para os quais foram detectadas inconsistências de informações. 
* `wrong_date`: Dados agregados contemplando os microdados para os quais não foram detectadas inconsistências de informações exceto pela data, que está fora do real período de vacinação.

Os dados estão em arquivos separados de acordo com a semana de aplicação das vacinas. O nome de cada arquivo é a data da segunda-feira da semana correspondente. Por exemplo, os dados entre os dias 5 de julho de 2021 e 11 de julho de 2021 estão todos em um arquivo intitulado `2021-07-05.csv`. Chamamos essa data de semana-índice.

## Como baixar

* Para baixar todos os dados em um arquivo compactado, acesse [este link](https://github.com/raphsilva/data-covid-vaccination-brazil/archive/refs/heads/master.zip). O tamanho do arquivo é 51,4 MB em 4 de julho de 2021.

* Para baixar alguns dados específicos, filtrando por data ou unidade federativa, veja o código disponível em [clean-data-covid-vaccination-brazil/downloader.py](https://github.com/raphsilva/clean-data-covid-vaccination-brazil/blob/master/downloader.py).

## Seções

As seções abaixo descrevem como ler os dados dentro do diretório `data`:

### `_info`

O diretório `_info` contém:

* Um arquivo `totals.csv` que contém o número total de vacinas aplicadas em cada data, sumarizando os dados disponíveis neste repositório. 
* Um diretório `update_totals`, que contém um arquivo para cada semana-índice. Cada arquivo registra as datas em que os dados correspondente foram atualizados, e a contagem total de vacinas aplicadas em cada data de atualização.

### `consistent`

O diretório `consistent` contém os dados agregados. Ele contém vários arquivos CSV cujos nomes são correspondentes às semanas-índices. Cada arquivo contém os seguintes campos, nomeados conforme a documentação do OpenDataSus: 
* paciente_enumSexoBiologico
* paciente_idade 
* vacina_nome
* vacina_categoria_nome
* vacina_grupoAtendimento_nome

Além desses campos, há uma coluna `dose` que informa com um número inteiro se a dose aplicada foi a primeira ou a segunda. 

A coluna `contagem` informa quantas vezes a combinação de dados daquela linha ocorreu na data de vacinação correspondente. 

A coluna `data_aplicaçao` informa a data de aplicação da vacina.

### `inconsistent`

O diretório `inconsistent` contém dados com possíveis problemas de consistência. Eles estão dispostos da mesma forma que os do diretório `consistent`, exceto que contêm uma coluna extra chamada `paciente_id` para facilitar a análise de IDs duplicados. 

### `wrong_date`

O diretório `wrong_date` contém os dados cujas datas estão claramente erradas. Sua organização é idêntica ao do diretório `consistent`.