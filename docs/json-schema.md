# 📦 JSON Output Schema

Este documento descreve a estrutura do JSON retornado pelo módulo de IA responsável pela classificação de leads.

O modelo é obrigado a retornar exclusivamente um objeto JSON válido, seguindo o schema previamente definido.

---

# 🎯 Objetivo

Garantir:

- Padronização
- Consistência
- Integração futura com CRM ou BI
- Redução de ambiguidade da IA

---

# 🧩 Estrutura Geral

O objeto é dividido em 5 blocos principais:

1. Dados Cadastrais
2. Contatos e Presença Digital
3. Análise Inteligente
4. Scoring
5. Metadados de Confiança

---

# 📄 Principais Campos

## Dados Empresariais

- razao_social (string)
- cnpj (string)
- porte (string)
- ramo (string)
- capital_social (string)
- municipio_matriz (string)
- uf (string)

---

## Contato

- telefone_google (string)
- telefone_matriz (string)
- email (string)
- website (string)

---

## Presença Digital

- ranking_google (number)
- presenca_digital (object)
- redes_sociais (array)

---

## Classificação

- overall_score (number 0–100)
- bucket (frio | morno | quente)
- potencial_comercial (baixo | médio | alto)
- potencial_digital (baixo | médio | alto)

---

## Transparência

- signals_positive (array)
- signals_negative (array)
- missing_fields (array)
- rationale (string)
- confidence (number 0–1)

---

# 📌 Campos Obrigatórios

Os seguintes campos não podem ser omitidos:

- razao_social
- cnpj
- situacao
- porte
- ramo
- municipio_matriz
- email
- website
- ranking_google
- overall_score
- bucket
- potencial_comercial
- potencial_digital
- confidence
- rationale

---

# 🧠 Observação

O modelo foi instruído a:

- Não omitir campos inexistentes
- Preencher com string vazia quando necessário
- Nunca utilizar markdown
- Nunca incluir texto fora do objeto JSON

---
© 2026 Rayana Santos — All rights reserved.
