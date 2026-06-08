# 📊 Quais fatores mais influenciam o salário de um profissional de dados no Brasil em 2024?

**Trabalho Final — Análise Avançada de Dados**
**Centro Universitário Santo Agostinho — UNIFSA | Engenharia de Software**
**Profa. Ma. Heloisa Guimarães | Junho de 2026**

**Autoras:** Yasmin Moreira & Thayanne Oliveira

---

## 📌 Resposta à Pergunta Central

Os dois fatores de maior impacto no salário de um profissional de dados no Brasil em 2024 são **senioridade** e **experiência em dados**, nessa ordem. Juntos, eles explicam a maior parte da variação salarial observada (Spearman: rho = 0,734 e rho = 0,658, respectivamente, ambos com p < 0,001).

Região e gênero também influenciam, mas com magnitude significativamente menor. O perfil de maior salário mediano é o de um profissional **Sênior, com mais de 7 anos de experiência, atuando no Sul ou Sudeste** — com salário mediano de R$ 14.000, contra R$ 3.500 de um profissional Júnior sem experiência.

---

## 🗂️ Estrutura do Repositório

```
yasmin-thayanne-state-of-data/
├── README.md
├── notebook/
│   └── Thayanne-Yasmin-analise.ipynb
├── relatorio/
│   └── yasmin-thayanne-relatorio.pdf
└── dados/
    └── README.md   ← instruções para baixar a base (CSV não incluído)
```

---

## 📁 Sobre os Dados

| Item | Detalhe |
|------|---------|
| **Fonte** | State of Data Brazil 2024–2025 |
| **Organizadores** | Data Hackers & Bain & Company |
| **Respondentes** | 5.217 |
| **Colunas** | 403 |
| **Base final (após limpeza)** | 4.863 respondentes |
| **Download** | [kaggle.com/datasets/datahackers/state-of-data-brazil-20242025](https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-20242025) |

> ⚠️ O arquivo CSV **não está incluído** no repositório. Faça o download diretamente pelo Kaggle e salve em `dados/` antes de rodar o notebook.

---

## 🧹 Principais Decisões de Limpeza

| Problema | Decisão adotada |
|----------|----------------|
| Faixas salariais em texto (ex: "de R$4.001 a R$6.000") | Convertidas para ponto médio (ex: R$ 5.000,50). Extremos: R$ 500 e R$ 45.000 |
| Colunas com nomes crípticos (ex: `2.h_faixa_salarial`) | Renomeadas com base no dicionário oficial do Kaggle — 14 colunas-chave |
| Inconsistência de cargo/título ("Analista de Dados", "Data Analyst") | Mapeamento explícito para 11 categorias padronizadas; demais agrupados como "Outro" |
| Missings em gênero e raça/cor | **Não imputados** — ausência intencional tratada como dado sensível |
| 354 respondentes sem salário (6,8%) | Removidos após conversão das faixas |

Todas as decisões estão documentadas em células Markdown no notebook, com critério adotado e impacto estimado.

---

## 📈 Principais Achados

### 1. Distribuição salarial assimétrica
- **Mediana: R$ 10.000** | Média: R$ 12.029 | Desvio padrão: R$ 8.997
- Assimetria à direita (1,61): a maioria ganha abaixo da média. A mediana é a medida mais representativa.

### 2. Senioridade — maior impacto isolado (rho = 0,734)
| Nível | Salário Mediano | Variação vs Júnior |
|-------|----------------|-------------------|
| Júnior | R$ 3.500 | — |
| Pleno | R$ 7.000 | +100% |
| Sênior | R$ 14.000 | +300% |

### 3. Experiência amplifica a senioridade (rho = 0,658)
- De R$ 3.500 (< 1 ano) a R$ 18.000 (> 10 anos)
- Salto mais expressivo entre 2–4 anos e 5–6 anos de experiência

### 4. Região — diferença de ~43%
- Sul e Sudeste: mediana de **R$ 10.000**
- Centro-Oeste, Norte e Nordeste: mediana de **R$ 7.000**

### 5. Gênero — paridade bruta, desigualdade estrutural
- Mediana bruta: **R$ 10.000 para ambos** (diferença = 0%)
- Controlado por senioridade: no nível Sênior, homens têm mediana de R$ 14.000 vs **R$ 10.000 das mulheres** (diferença de 40%)

---

## ⚙️ Como Reproduzir a Análise

1. **Clone o repositório**
```bash
git clone https://github.com/yasmin-thayanne/yasmin-thayanne-state-of-data.git
cd yasmin-thayanne-state-of-data
```

2. **Baixe a base de dados** no [Kaggle](https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-20242025) e salve o CSV em `dados/`

3. **Instale as dependências**
```bash
pip install pandas numpy matplotlib seaborn scipy
```

4. **Abra o notebook**
```bash
jupyter notebook notebook/yasmin-thayanne-analise.ipynb
```
> O notebook também pode ser aberto diretamente no [Google Colab](https://colab.research.google.com).

---

## 🛠️ Bibliotecas Utilizadas

| Biblioteca | Uso |
|-----------|-----|
| `pandas` | Leitura, limpeza e manipulação dos dados |
| `numpy` | Cálculos numéricos e conversão de faixas |
| `matplotlib` | Visualizações (histograma, boxplot, barras, linha) |
| `seaborn` | Heatmap e estilização dos gráficos |
| `scipy.stats` | Correlação de Spearman |

---

## ⚠️ Limitações e Ética

- **Correlação, não causalidade:** todas as relações identificadas são correlacionais.
- **Viés de auto-seleção:** respondentes voluntários da comunidade Data Hackers podem não representar o setor completo.
- **Imprecisão das faixas:** a conversão para ponto médio introduz erro de até ~R$ 2.000 por faixa.
- **Dados sensíveis não imputados:** missings em gênero e raça/cor foram mantidos como ausência intencional, discutidos no relatório.
- Os dados sobre desigualdade por gênero e raça têm implicações sociais reais e devem ser usados para identificar onde intervenções são necessárias — não para reforçar estereótipos.

---

## 📄 Referências

- DATA HACKERS; BAIN & COMPANY. *State of Data Brazil 2024–2025.* Kaggle, 2024.
- PANDAS DEVELOPMENT TEAM. *pandas: Python Data Analysis Library.* v. 2.x, 2024.
- HUNTER, J. D. Matplotlib: A 2D Graphics Environment. *Computing in Science & Engineering,* v. 9, n. 3, 2007.
- WASKOM, M. seaborn: statistical data visualization. *Journal of Open Source Software,* v. 6, n. 60, 2021.
- SCIPY COMMUNITY. *SciPy: Open Source Scientific Tools for Python.* v. 1.x, 2024.

---
