# 📈 Análise de Ações Brasileiras com Python — B3 (2023–2026)

Projeto acadêmico desenvolvido em Python no Google Colab para análise histórica de ações da B3. O notebook coleta, processa e visualiza dados de **5 empresas brasileiras de grande porte** entre janeiro de 2023 e maio de 2026, aplicando conceitos de estatística e finanças com as principais bibliotecas de análise de dados em Python.

> 📌 Disciplina: Análise de Dados aplicada à Administração — 3º período

---

## 🏢 Empresas Analisadas

| Empresa | Ticker | Segmento |
|---|---|---|
| Petrobrás | PETR4.SA | Energia / Petróleo |
| Vale S.A. | VALE3.SA | Mineração |
| Ambev S.A. | ABEV3.SA | Bebidas / Consumo |
| Itaú Unibanco | ITUB4.SA | Financeiro / Bancos |
| Banco do Brasil | BBAS3.SA | Financeiro / Bancos |

---

## 🗂️ Estrutura do Notebook

O notebook está dividido em **duas partes principais**:

### Parte 1 — Análise da Petrobrás (código de referência)
Bloco completo e detalhado com cada etapa comentada, servindo como modelo para entender a lógica aplicada. Inclui todas as 7 etapas descritas abaixo.

### Parte 2 — Análise das demais 4 empresas (função reutilizável)
Para evitar repetição de código, as etapas foram encapsuladas em uma função chamada `analisar_empresa()`, que recebe o ticker e o nome da empresa e executa toda a análise automaticamente. A função é chamada uma vez para cada empresa:

```python
df_vale  = analisar_empresa("VALE3.SA",  "Vale S.A.")
df_ambev = analisar_empresa("ABEV3.SA",  "Ambev S.A.")
df_itau  = analisar_empresa("ITUB4.SA",  "Itaú Unibanco")
df_bb    = analisar_empresa("BBAS3.SA",  "Banco do Brasil")
```

---

## 🔍 Etapas da Análise (por empresa)

**1. Download dos dados históricos**
Os dados são coletados diretamente do Yahoo Finance pela biblioteca `yfinance`, com as colunas renomeadas para português: Abertura, Máxima, Mínima, Fechamento e Volume.

**2. Visualização dos dados**
São exibidas as 5 primeiras e as 5 últimas linhas do DataFrame, permitindo conferir o período coberto e a estrutura dos dados.

**3. Média anual do preço de fechamento**
Calculada para cada ano do período (2023, 2024, 2025 e 2026), indicando o patamar médio de preço em cada ano.

**4. Desvio-padrão anual**
Mede a volatilidade do preço de fechamento em cada ano — quanto maior, mais instável foi o comportamento da ação naquele período.

**5. Retorno semestral**
Calcula a variação percentual do preço de fechamento entre semestres consecutivos, usando o último dia útil de cada semestre como referência:

$$\text{Retorno} = \frac{\text{Fechamento}_{S+1} - \text{Fechamento}_{S}}{\text{Fechamento}_{S}} \times 100$$

Exemplo de saída:
```
2023_S1 → 2023_S2: -5.42%
2023_S2 → 2024_S1: +11.78%
2024_S1 → 2024_S2: -3.21%
```

**6. Gráfico de linha com eixo semestral**
Gera um gráfico do preço de fechamento ao longo do tempo, com o eixo X marcado apenas pelos semestres (2023-S1, 2023-S2, 2024-S1...) e pontos destacados em roxo no fim de cada semestre.

**7. Tabela resumo semestral + resumo final**
Tabela consolidada com, para cada semestre: preço de abertura, fechamento, média, desvio-padrão, mínimo, máximo e retorno percentual. Seguida de um resumo final com o retorno total acumulado no período e o volume médio diário de negociações.

---

## 🛠️ Tecnologias e Bibliotecas

| Biblioteca | Para que serve no projeto |
|---|---|
| `yfinance` | Baixar dados históricos de ações do Yahoo Finance |
| `pandas` | Criar e manipular tabelas (DataFrames) |
| `matplotlib` | Gerar os gráficos de linha |
| `seaborn` | Aplicar estilo visual aos gráficos |

---

## ▶️ Como executar

O projeto roda inteiramente no navegador via **Google Colab** — sem precisar instalar nada no computador.

1. Abra o notebook pelo link do Google Colab
2. Clique em **Runtime → Run all** (ou pressione `Ctrl + F9`)
3. Aguarde o download dos dados e a geração dos gráficos

As bibliotecas são instaladas automaticamente na primeira célula:

```python
!pip install yfinance pandas matplotlib seaborn -q
```

---

## 📐 Conceitos Financeiros Utilizados

**Preço de fechamento:** valor final da ação ao término do pregão, a referência mais usada em análises financeiras.

**Média:** indica o preço central em torno do qual a ação oscilou em determinado período.

**Desvio-padrão:** quanto maior, mais a ação variou de preço — ou seja, maior o risco para o investidor.

**Retorno semestral:** mostra se a ação valorizou ou desvalorizou de um semestre para o outro, em termos percentuais.

**Semestre S1:** janeiro a junho. **Semestre S2:** julho a dezembro.

---

## 📁 Arquivos do Repositório

```
📄 analise_acoes.ipynb   ← Notebook completo com todas as análises
📄 README.md             ← Este arquivo
```

---

*Projeto desenvolvido para fins acadêmicos. Dados obtidos via Yahoo Finance através da biblioteca yfinance.*
