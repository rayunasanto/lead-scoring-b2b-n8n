# 🏗️ Architecture Overview

Este projeto implementa um pipeline automatizado de enriquecimento, validação e classificação de leads B2B utilizando APIs públicas, scraping estruturado e um módulo de IA para scoring inteligente.

A arquitetura foi desenhada com foco em:

- Baixo custo operacional
- Modularidade
- Reprocessamento inteligente
- Escalabilidade futura
- Redução de chamadas desnecessárias a APIs

---

# 🔄 Visão Geral do Fluxo

O fluxo foi desenvolvido no n8n e dividido em 5 grandes camadas:

1. Ingestão de Dados
2. Validação Cadastral
3. Deduplicação Inteligente
4. Enriquecimento Digital
5. Classificação e Scoring com IA

---

# 1️⃣ Ingestão de Dados

**Fonte inicial:**
- Planilha contendo CNPJs

Para cada CNPJ:
- Consulta API da Receita Federal
- Consulta API do Google Maps

Objetivo:
Obter dados cadastrais, localização, telefone, website e reputação inicial.

---

# 2️⃣ Validação Cadastral

Após captura:

- Se CNPJ não encontrado → descartado
- Se situação ≠ ATIVA → descartado
- Se válido → segue para próxima etapa

Essa etapa reduz ruído e garante qualidade da base.

---

# 3️⃣ Deduplicação Inteligente

Antes de qualquer processamento adicional:

- Verifica se o CNPJ já foi processado anteriormente
- Caso já exista na base → ignora e segue para o próximo
- Caso não exista → continua o fluxo

Isso evita:
- Chamadas repetidas a APIs
- Custo desnecessário
- Retrabalho computacional

---

# 4️⃣ Enriquecimento Digital

Se o Google Maps retornar um website:

- O sistema acessa o site
- Executa leitura estrutural via API HTML
- Extrai conteúdo relevante para análise

Se não houver website:
- O fluxo continua normalmente
- Apenas com os dados já coletados

Objetivo:
Aumentar a profundidade da análise para melhorar o scoring.

---

# 5️⃣ Classificação e Scoring com IA

Após consolidação dos dados:

O módulo de IA é acionado para:

- Analisar dados cadastrais
- Avaliar aderência ao segmento (construção civil)
- Identificar maturidade digital
- Gerar score de 0 a 100
- Classificar em:
  - Lead Frio (0–59)
  - Lead Morno (60–79)
  - Lead Quente (80–100)

## Modelo utilizado

- OpenRouter (modelo open-source)
- Escolha estratégica para manter custo zero

---

# 🧠 Lógica de Pontuação

A pontuação é distribuída da seguinte forma:

- Regularidade Cadastral → 25 pontos
- Contato Digital → 25 pontos
- Estabilidade (idade + capital) → 20 pontos
- Potencial Comercial → 20 pontos
- Reputação Online → 10 pontos

Total máximo: 100 pontos

---

# 📦 Estrutura de Dados

O retorno da IA é rigidamente estruturado em JSON,
seguindo um schema previamente definido para garantir:

- Padronização
- Consistência
- Fácil integração futura com CRM ou BI

---

# 💰 Estratégia de Baixo Custo

O projeto foi desenhado para:

- Utilizar APIs públicas
- Minimizar requisições duplicadas
- Utilizar modelo open-source
- Evitar processamento desnecessário

---

# 🚀 Possíveis Evoluções

- Persistência em banco relacional
- Criação de API REST própria
- Dashboard em Power BI
- Integração automática com CRM
- Monitoramento e logging estruturado
- Cache distribuído

---

# 📊 Arquitetura Resumida

Planilha → Receita Federal API → Google Maps API  
→ Validação → Deduplicação  
→ (Opcional) Website Scraping  
→ Módulo IA  
→ JSON Estruturado  
→ Base de Leads Classificada

---

# 🎯 Objetivo Final

Gerar uma base qualificada de leads B2B,
priorizada por potencial de conversão,
reduzindo esforço manual do time comercial.

---
© 2026 Rayana Santos — All rights reserved.
