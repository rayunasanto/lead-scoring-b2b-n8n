# 📊 Scoring Logic

Este documento descreve a lógica utilizada para classificar e priorizar leads B2B com base em critérios cadastrais, comerciais e digitais.

O modelo combina regras determinísticas (pontuação fixa) com análise contextual via IA.

---

# 🎯 Objetivo do Scoring

Gerar um score de 0 a 100 que represente o potencial de conversão comercial do lead, classificando-o em:

- 🔴 Frio → 0 a 59
- 🟡 Morno → 60 a 79
- 🟢 Quente → 80 a 100

---

# 🧩 Estrutura de Pontuação

A pontuação total é composta por 5 blocos independentes:

| Critério | Peso Máximo |
|----------|------------|
| Regularidade Cadastral | 25 pontos |
| Contato Digital | 25 pontos |
| Estabilidade Empresarial | 20 pontos |
| Potencial Comercial | 20 pontos |
| Reputação Online | 10 pontos |
| **Total Máximo** | **100 pontos** |

---

# 1️⃣ Regularidade Cadastral (25 pontos)

Critérios avaliados:

- Situação cadastral = ATIVA
- Natureza jurídica válida
- Porte definido

Se todos os critérios forem atendidos → +25 pontos  
Caso contrário → 0 pontos

Objetivo: garantir formalização mínima da empresa.

---

# 2️⃣ Contato Digital (25 pontos)

Critérios avaliados:

- Telefone disponível
- Email disponível
- Website disponível
- Horário de funcionamento
- Sócios identificados

Quanto mais campos preenchidos, maior a robustez do lead.

Se conjunto completo → +25 pontos

Objetivo: medir facilidade de contato e maturidade operacional.

---

# 3️⃣ Estabilidade Empresarial (20 pontos)

Critérios avaliados:

- Data de abertura
- Tempo de operação
- Capital social declarado

Empresas mais antigas e com capital estruturado recebem maior pontuação.

Objetivo: reduzir risco comercial.

---

# 4️⃣ Potencial Comercial (20 pontos)

Critérios avaliados:

- Segmento aderente à construção civil
- Atuação em materiais de construção, engenharia ou revenda
- Localização estratégica

Se altamente aderente → +20 pontos

Objetivo: garantir fit com o ICP (Ideal Customer Profile).

---

# 5️⃣ Reputação Online (10 pontos)

Critérios avaliados:

- Presença no Google Maps
- Ranking disponível
- Avaliações de clientes

Se reputação identificada → +10 pontos

Objetivo: medir presença pública e confiabilidade.

---

# 🧠 Papel da IA

Após consolidação dos dados, o módulo de IA:

- Analisa coerência das informações
- Ajusta classificação contextual
- Gera resumo analítico
- Define bucket final (frio, morno, quente)
- Indica próximas ações

A IA opera sob restrições rígidas de saída JSON para garantir padronização e evitar alucinação.

---

# 📌 Buckets de Classificação

| Score | Classificação |
|-------|--------------|
| 0 – 59 | Frio |
| 60 – 79 | Morno |
| 80 – 100 | Quente |

---

# 🔍 Transparência e Auditabilidade

O retorno estruturado inclui:

- signals_positive
- signals_negative
- missing_fields
- rationale
- confidence

Isso permite:

- Auditoria posterior
- Ajuste de pesos futuros
- Explicabilidade do modelo

---

# 🚀 Possíveis Evoluções

- Ajuste dinâmico de pesos
- Modelo híbrido com aprendizado supervisionado
- Persistência histórica para análise temporal
- A/B testing de critérios

---

# 👩🏻‍💻 Author

Rayana Aparecida  
Engenharia de Dados | Automação | IA aplicada a negócios
