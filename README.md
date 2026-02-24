# 🚀 Automação Inteligente de Lead Scoring B2B

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

## 👩🏻‍💻 Sobre

Desenvolvido por Rayana Santos  
Engenharia de Dados | Automação | IA aplicada a negócios
