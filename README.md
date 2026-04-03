# 🧠 TalentAI — Sistema Inteligente de Triagem de Candidatos

> Automação completa de recrutamento com Inteligência Artificial, integrada a dashboards analíticos para apoio à decisão no RH.

---

## 📌 Sobre o Projeto

O **TalentAI** é um sistema end-to-end de triagem de currículos que utiliza IA generativa para analisar candidatos, gerar scores de compatibilidade e alimentar dashboards em tempo real — sem intervenção humana.

### O problema que resolve

| Antes | Depois |
|---|---|
| ❌ Triagem manual e demorada | ✅ Análise automática em segundos |
| ❌ Critérios subjetivos | ✅ Score padronizado por IA |
| ❌ Sem rastreabilidade | ✅ Histórico completo na planilha |
| ❌ Dashboards desatualizados | ✅ Indicadores em tempo real |

---

## 🏗️ Arquitetura do Sistema

```
Recrutador acessa a página (Lovable)
        ↓
Preenche nome da vaga + currículo
        ↓
Webhook recebe os dados (n8n)
        ↓
Busca requisitos da vaga (Google Sheets — aba Vagas)
        ↓
IA analisa e gera score (Google Gemini 2.5)
        ↓
CV arquivado como .txt (Google Drive — pasta TalentAI_CVs)
        ↓
Resultado salvo com link do CV (Google Sheets — aba Candidatos)
        ↓
Dashboard atualizado automaticamente (Power BI)
```

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Função |
|---|---|
| **Lovable** | Interface web profissional para envio de currículos |
| **n8n Cloud** | Orquestração de toda a automação |
| **Google Gemini 2.5** | Análise de currículos e geração de score com IA |
| **Google Sheets** | Base de dados de candidatos e requisitos de vagas |
| **Google Drive** | Arquivo dos currículos originais em .txt |
| **Power BI** | Dashboards analíticos para o time de RH |

---

## ⚙️ Como Funciona

### 1. 🖥️ Interface de Envio (Lovable)
O recrutador acessa a página do TalentAI, informa o nome da vaga e cola o currículo do candidato. A página envia os dados automaticamente via webhook para o n8n.

### 2. ⚙️ Automação (n8n)
O n8n orquestra todo o fluxo em sequência:
- Recebe os dados pelo webhook
- Busca os requisitos da vaga na planilha
- Envia para análise da IA
- Arquiva o CV no Google Drive
- Salva o resultado na planilha

### 3. 🤖 Análise com IA (Google Gemini 2.5)
O Gemini recebe o currículo completo junto com os requisitos obrigatórios e desejáveis da vaga e retorna uma análise estruturada com:
- Score de compatibilidade (0 a 100)
- Categoria de aderência
- Competências identificadas
- Lacunas em relação à vaga
- Observação para o recrutador

### 4. 📊 Base de Dados (Google Sheets)
O projeto utiliza duas abas na planilha:

**Aba Vagas** — requisitos de cada posição:
| Nome da Vaga | Requisitos Obrigatórios | Requisitos Desejáveis | Nível | Experiência Mínima |
|---|---|---|---|---|
| Analista de dados | Python, SQL, Power BI, Excel | Machine Learning, Tableau | Pleno | 2 anos |
| Desenvolvedor backend | Python, Docker, REST API, PostgreSQL | Kubernetes, Redis | Pleno | 3 anos |
| UX designer | Figma, User Research, Prototipagem | Motion Design, Design System | Júnior/Pleno | 1 ano |

**Aba Candidatos** — resultado de cada análise:
| Campo | Descrição |
|---|---|
| ID | Sequencial automático |
| Nome do Candidato | Extraído do currículo pela IA |
| Vaga | Nome da vaga analisada |
| Data da Análise | Gerada automaticamente |
| Score (%) | 0 a 100 |
| Categoria | Altamente / Parcialmente / Não Aderente |
| Competências Identificadas | Skills encontradas no CV |
| Lacunas | O que falta para a vaga |
| Observação da IA | Análise em 1-2 frases |
| Analista | "IA Gemini" (automático) |
| Status Final | "Em avaliação" (padrão) |
| Link do CV | Link direto para o arquivo no Google Drive |

### 5. 🗄️ Arquivo de CVs (Google Drive)
Cada currículo analisado é salvo automaticamente como arquivo **.txt** no Google Drive, na pasta **TalentAI_CVs**. O link direto é salvo na planilha para acesso rápido pelo recrutador.

### 6. 🎯 Classificação de Candidatos

| Categoria | Score | Significado |
|---|---|---|
| 🟢 Altamente Aderente | ≥ 70 | Atende os principais requisitos |
| 🟡 Parcialmente Aderente | 40 a 69 | Atende parte dos requisitos |
| 🔴 Não Aderente | < 40 | Não atende os requisitos mínimos |

---

## 📊 Dashboard Power BI

Painel único com todas as métricas em uma página com tema TalentAI:

**KPIs:**
- Total de Candidatos
- Média de Score
- Altamente Aderentes
- Não Aderentes

**Gráficos:**
- 🥧 Distribuição por Categoria (pizza)
- 📊 Candidatos por Vaga (barras)
- 🏆 Ranking de Candidatos (tabela ordenada por score com formatação condicional)

---

## 🖼️ Prints do Projeto

### Interface de Envio (Lovable)
![Lovable](prints/01_lovable_formulario.png)

### Fluxo de Automação (n8n)
![n8n](prints/03_fluxo_n8n.png)

### Planilha de Candidatos (Google Sheets)
![Planilha](prints/06_planilha_candidatos.png)

### CVs Arquivados (Google Drive)
![Drive](prints/07_google_drive.png)

### Dashboard (Power BI)
![Power BI](prints/08_power_bi.png)

---

## 🗂️ Estrutura do Repositório

```
TalentAI/
├── README.md
└── prints/
    ├── 01_lovable_formulario.png
    ├── 02_lovable_sucesso.png
    ├── 03_fluxo_n8n.png
    ├── 04_prompt_gemini.png
    ├── 05_planilha_vagas.png
    ├── 06_planilha_candidatos.png
    ├── 07_google_drive.png
    └── 08_power_bi.png
```

---

## 🎯 Resultados

- ⚡ Análise completa de currículo em menos de 10 segundos
- 📋 Score e classificação gerados automaticamente pela IA
- 🗄️ CV arquivado no Google Drive com link direto na planilha
- 📈 Dashboard atualizado a cada novo candidato analisado
- 🔗 Fluxo 100% automatizado sem intervenção humana

---

## 👨‍💻 Sobre o Autor

Projeto desenvolvido para demonstrar habilidades práticas em:

- Automação de processos com **n8n**
- Integração de **IA generativa** em fluxos reais
- Análise e visualização de dados com **Power BI**
- Desenvolvimento de interfaces com **Lovable**
- Integração entre múltiplas plataformas e APIs

---

> 💡 *Este projeto foi desenvolvido com fins educacionais e de portfólio.*
> *Detalhes técnicos de implementação disponíveis mediante contato.*
