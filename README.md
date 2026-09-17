# Monkey Growth Case

Análise de dados desenvolvida para identificar oportunidades de crescimento em uma plataforma de antecipação de recebíveis.

O trabalho busca responder a duas questões principais:

1. Como aumentar o volume antecipado?
2. Como aumentar o número de fornecedores cadastrados e ativos?

A análise considera que o crescimento não depende somente da aquisição de novos fornecedores, mas de todo o funil:

**oportunidade disponível → conhecimento → cadastro → primeira antecipação → recorrência e volume**

---

## Principais resultados

- Aproximadamente **R$ 51,5 bilhões** em volume antecipado no período analisado.
- **7.648 fornecedores** realizaram pelo menos uma operação.
- Os **10% maiores fornecedores concentram cerca de 79% do volume**.
- Fornecedores do segmento **Tiny representam aproximadamente 36% do volume**.
- Cerca de **16,6 mil fornecedores** aparecem na base de conversão sem data de cadastro.
- **2.532 fornecedores cadastrados** tiveram possibilidade de operar, mas nunca realizaram uma antecipação.
- A conversão média entre fornecedores cadastrados e elegíveis ficou próxima de **50%**.

Também foram encontradas questões relevantes de qualidade:

- **7.298 duplicatas exatas** na base original de conversão;
- **128 valores nulos** na coluna de conversão;
- registros com conversão positiva antes ou sem uma data de cadastro compatível.

As duplicatas foram removidas somente da camada analítica. Os dados originais foram preservados.

---

## Recomendações de Growth

### 1. Cadastro no momento de maior intenção

Acionar fornecedores ainda não cadastrados sempre que uma nova oportunidade de antecipação estiver disponível.

**Métrica principal:** cadastros por fornecedores expostos.

### 2. Ativação de fornecedores cadastrados

Criar uma jornada específica para os 2.532 fornecedores que tiveram possibilidade de operar, mas nunca realizaram uma antecipação.

**Métrica principal:** primeira operação em até 30 dias.

### 3. Jornada dos primeiros 90 dias

Estruturar uma régua de onboarding e comunicação para estimular primeira operação e recorrência.

**Métricas principais:**

- tempo até a primeira operação;
- conversão em 30, 60 e 90 dias;
- recorrência;
- volume antecipado por fornecedor.

### 4. Estratégia para Tiny e cauda longa

Acompanhar simultaneamente volume financeiro e quantidade de fornecedores ativos, evitando que o crescimento dependa apenas das maiores contas.

### 5. Atuação conjunta com Sacados

Priorizar Sacados com grande quantidade de fornecedores expostos ainda não cadastrados e acompanhar a frequência das oportunidades disponibilizadas.

---

## Estrutura do projeto

```text
monkey-growth-case/
├── data/
│   ├── raw/
│   │   └── Case_monkey.xlsx
│   ├── processed/
│   │   ├── operacao_tratada.csv
│   │   ├── conversao_tratada.csv
│   │   └── cadastro_tratado.csv
│   └── README.md
├── docs/
│   └── conclusoes.md
├── notebooks/
│   └── Monkey_Growth_Case.ipynb
├── outputs/
│   ├── figures/
│   ├── tables/
│   └── README.md
├── .gitignore
└── README.md
```

---

## Organização das camadas

```text
data/raw
```
Contém o arquivo original disponibilizado para o case, sem alterações.

```text
data/processed
```
Contém as bases tratadas, com:

- padronização de datas;
- limpeza dos campos textuais;
- criação de variáveis analíticas;
- classificação do status de cadastro;
- remoção de duplicatas exatas da base de conversão.

```text
outputs/tables
```
Contém os resultados consolidados, incluindo:

- resumo executivo;
- indicadores de qualidade;
- volume mensal;
- análise por segmento;
- concentração de volume;
- funil de cadastro e ativação;
- conversão mensal;
- conversão por tempo desde o cadastro;
- coortes;
- registros separados para auditoria.

```text
outputs/figures
```
Contém os gráficos utilizados no diagnóstico e na apresentação dos resultados.

```text
docs
```
Contém as conclusões, recomendações e limitações da análise.

---

## Como executar

O projeto foi desenvolvido em Python e pode ser executado no Google Colab.

1. Clonar o repositório

```text
!git clone URL_DO_REPOSITORIO
%cd monkey-growth-case
```

Substitua URL_DO_REPOSITORIO pela URL deste repositório.

2. Abrir o notebook

Abra:

```text
notebooks/Monkey_Growth_Case.ipynb
```

3. Executar as células

Execute as células na ordem apresentada.

O notebook utiliza principalmente:

- Python;
- pandas;
- NumPy;
- Matplotlib;
- pathlib.

As pastas necessárias são criadas automaticamente.

---

## Resultados gerados

Ao final da execução, o notebook produz:

- 3 bases tratadas em data/processed;
- 15 tabelas analíticas em outputs/tables;
- 7 visualizações em outputs/figures;
- arquivo de conclusões em docs/conclusoes.md.

---

## Priorização

Prioridade	Iniciativa	Impacto	Confiança	Esforço

1	Convite acionado por oportunidade disponível	Alto	Alta	Médio
2	Ativação de cadastrados com oportunidade	Alto	Alta	Médio
3	Jornada dos primeiros 90 dias	Alto	Média	Médio
4	Segmentação Tiny e cauda longa	Médio	Média	Médio
5	Expansão em parceria com Sacados	Alto	Média	Alto

---

## Limitações

A base não contém todos os dados necessários para estimar causalidade ou retorno financeiro incremental.

Para uma análise mais completa, seriam necessários:

- valor disponibilizado por fornecedor;
- identificação do Sacado;
- taxas e condições ofertadas;
- histórico de comunicações;
- canal de aquisição;
- data da primeira operação;
- recorrência;
- custos de campanha e incentivos.

As coortes mais recentes também possuem menor janela de observação. Por isso, a taxa histórica de fornecedores que já operaram não deve ser comparada diretamente entre coortes sem controlar o tempo disponível para conversão.

---

## Conclusão

A principal oportunidade não está somente em aumentar o número bruto de cadastros.

Os dados indicam duas frentes prioritárias:

1. converter fornecedores que já foram expostos a oportunidades, mas ainda não estão cadastrados;
2. ativar fornecedores cadastrados que tiveram possibilidade de operar, mas nunca realizaram uma antecipação.

Esses grupos possuem público identificável, permitem experimentação controlada e apresentam potencial de impacto tanto no número de fornecedores ativos quanto no volume antecipado.

---

Autora

Bettina Vilela Custódio

Projeto desenvolvido como parte de um case de Growth Analytics.
