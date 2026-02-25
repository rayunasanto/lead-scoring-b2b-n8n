# 🚀 PT BR - Automação Inteligente de Lead Scoring B2B

Projeto de automação desenvolvido no n8n com integração de APIs públicas e uso de Inteligência Artificial para classificação estratégica de leads no segmento B2B (construção civil e materiais).

---

## 📌 Objetivo

Criar um fluxo automatizado capaz de:

- Capturar dados empresariais via APIs
- Validar CNPJs automaticamente
- Enriquecer informações digitais (Google Maps + Website)
- Aplicar classificação inteligente via IA
- Gerar score de potencial comercial (0–100)
- Categorizar leads como: Frio, Morno ou Quente

O foco do projeto foi **baixo custo operacional com alta eficiência estratégica**.

---

## 🏗 Arquitetura do Projeto

O fluxo foi dividido em 4 grandes etapas:

### 1️⃣ Captura de Dados

- API Receita Federal → Dados cadastrais
- API Google Maps → Presença digital, telefone, avaliações, website

---

### 2️⃣ Validação

- Verificação de CNPJ ativo
- Descarte automático de registros inválidos
- Controle de duplicidade (evita reprocessamento)
- Armazenamento incremental da base

---

### 3️⃣ Enriquecimento Digital

- Identificação de website
- Extração de HTML
- Conversão para JSON estruturado
- Consolidação de dados cadastrais + digitais

---

### 4️⃣ Classificação com IA

Uso de modelo de IA (OpenRouter / modelo open-source) com prompt estruturado para:

- Análise cadastral
- Análise comercial
- Análise digital
- Avaliação de reputação online
- Cálculo de score estratégico

A resposta é forçada a retornar exclusivamente um JSON válido para garantir previsibilidade e integração segura.

---

## 🎯 Lógica de Pontuação

| Critério | Pontos |
|----------|--------|
| Formalização (CNPJ ativo, porte, natureza jurídica) | 25 |
| Contato digital (telefone, e-mail, site) | 25 |
| Estabilidade (tempo de mercado + capital social) | 20 |
| Potencial comercial (aderência ao setor) | 20 |
| Reputação online | 10 |

### Classificação Final

- 🔥 80–100 → Lead Quente
- 🌤 60–79 → Lead Morno
- ❄ 0–59 → Lead Frio

---

## 🧠 Estratégia de IA

O prompt foi cuidadosamente estruturado para:

- Evitar alucinação
- Proibir explicação da lógica interna
- Forçar resposta em JSON
- Manter consistência no schema
- Garantir previsibilidade de output

---

## 🛠 Stack Utilizada

- n8n (orquestração do fluxo)
- API Receita Federal
- API Google Maps
- Módulo de requisição HTML
- IA via OpenRouter
- Estrutura JSON padronizada

---

## 💡 Diferencial do Projeto

- Automação 100% escalável
- Baixo custo (uso de modelo gratuito)
- Controle de duplicidade
- Classificação orientada a negócio
- Estrutura modular

---

## 📊 Resultado Esperado

- Redução de tempo operacional na qualificação
- Priorização inteligente de leads
- Base estruturada para time comercial
- Decisão orientada por dados

---

## 🔮 Próximos Passos

- Dashboard em Power BI
- Treinamento supervisionado para refinar score
- Integração com CRM

---
© 2026 Rayana Santos — All rights reserved.


---
# 🚀 EN - Intelligent B2B Lead Scoring Automation

Automation project built with **n8n**, integrating public APIs and Artificial Intelligence for strategic lead classification in the B2B segment (construction and building materials industry).

---

## 📌 Objective

To create an automated workflow capable of:

- Capturing company data via public APIs  
- Automatically validating Brazilian business registrations (CNPJ)  
- Enriching digital presence data (Google Maps + Website)  
- Applying AI-based intelligent classification  
- Generating a commercial potential score (0–100)  
- Categorizing leads as: Cold, Warm or Hot  

The project focuses on **low operational cost with high strategic efficiency**.

---

## 🏗 Project Architecture

The workflow was structured into four major stages:

### 1️⃣ Data Collection

- Receita Federal API → Official company registration data  
- Google Maps API → Digital presence, phone, reviews, website  

---

### 2️⃣ Validation

- Active business registration (CNPJ) verification  
- Automatic discard of invalid records  
- Duplicate control (prevents reprocessing)  
- Incremental database storage  

---

### 3️⃣ Digital Enrichment

- Website identification  
- HTML extraction  
- Conversion into structured JSON  
- Consolidation of official + digital data  

---

### 4️⃣ AI-Based Classification

Use of an AI model (OpenRouter / open-source model) with a structured prompt for:

- Registration analysis  
- Commercial analysis  
- Digital presence analysis  
- Online reputation evaluation  
- Strategic scoring calculation  

The response is strictly enforced to return a valid JSON output to ensure predictability and safe system integration.

---

## 🎯 Scoring Logic

| Criteria | Points |
|----------|--------|
| Business formalization (active registration, company size, legal nature) | 25 |
| Digital contact availability (phone, email, website) | 25 |
| Business stability (market time + share capital) | 20 |
| Commercial potential (sector fit) | 20 |
| Online reputation | 10 |

### Final Classification

- 🔥 80–100 → Hot Lead  
- 🌤 60–79 → Warm Lead  
- ❄ 0–59 → Cold Lead  

---

## 🧠 AI Strategy

The prompt was carefully designed to:

- Minimize hallucinations  
- Prevent disclosure of internal reasoning  
- Enforce JSON-only output  
- Maintain schema consistency  
- Ensure predictable and structured responses  

---

## 🛠 Tech Stack

- n8n (workflow orchestration)  
- Receita Federal API  
- Google Maps API  
- HTML request module  
- OpenRouter (LLM integration)  
- Standardized JSON structure  

---

## 💡 Project Highlights

- Fully scalable automation  
- Low-cost architecture (free/open-source model usage)  
- Duplicate control mechanism  
- Business-oriented classification  
- Modular design  

---

## 📊 Expected Outcomes

- Reduced operational qualification time  
- Intelligent lead prioritization  
- Structured database for sales teams  
- Data-driven decision making  

---

## 🔮 Next Steps

- Power BI dashboard integration  
- Supervised model refinement  
- CRM integration  

---

© 2026 Rayana Santos — All rights reserved.
