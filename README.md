# 🚀 Automação Inteligente de Lead Scoring B2B

> Pipeline de automação no **n8n** que captura, valida, enriquece e classifica leads B2B do setor de **construção civil e materiais**, gerando um **score de potencial comercial (0–100)** com apoio de Inteligência Artificial.

<p align="left">
  <img src="https://img.shields.io/badge/n8n-Workflow_Automation-EA4B71?logo=n8n&logoColor=white" alt="n8n" />
  <img src="https://img.shields.io/badge/IA-OpenRouter-412991?logo=openai&logoColor=white" alt="OpenRouter" />
  <img src="https://img.shields.io/badge/API-Receita_Federal-1351B4" alt="Receita Federal" />
  <img src="https://img.shields.io/badge/API-Google_Maps-4285F4?logo=googlemaps&logoColor=white" alt="Google Maps" />
  <img src="https://img.shields.io/badge/Output-JSON_Schema-000000?logo=json&logoColor=white" alt="JSON Schema" />
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License" />
</p>

**🌐 Idioma:** **Português** · [English](README.en.md)

---

## 🎬 Visão Geral do Fluxo

<!--
  GIF do workflow rodando no n8n. Para gerar:
  1. Abra o workflow no n8n e clique em "Execute Workflow".
  2. Grave a tela (ScreenToGif no Windows, ou Kap/Gifox no Mac) por ~10-15s.
  3. Salve o arquivo como flow/demo.gif e remova o comentário da linha abaixo.
-->
<!-- ![Demonstração do workflow rodando](flow/demo.gif) -->

![Diagrama do fluxo no n8n](flow/flow-diagram.png)

O pipeline transforma uma **planilha de CNPJs** em uma **base de leads qualificada e priorizada**, pronta para o time comercial — com **custo operacional próximo de zero** (APIs públicas + modelo de IA open-source).

```
Planilha de CNPJs
      │
      ▼
Receita Federal API  +  Google Maps API      ← 1. Captura
      │
      ▼
Validação cadastral (CNPJ ativo?)            ← 2. Validação
      │
      ▼
Deduplicação (já processado?)                ← 3. Anti-retrabalho
      │
      ▼
Enriquecimento digital (scraping do site)    ← 4. Enriquecimento
      │
      ▼
Módulo de IA → score 0–100 + JSON            ← 5. Classificação
      │
      ▼
Base de Leads Classificada (🔥 / 🌤 / ❄)
```

---

## 🎯 O Problema que Resolve

Times comerciais B2B gastam horas qualificando leads manualmente — checando CNPJ, procurando site, avaliando porte e reputação. Este projeto **automatiza essa triagem** e entrega cada lead já pontuado e com **próximas ações sugeridas**, permitindo que o vendedor foque apenas nos leads com maior potencial de conversão.

---

## 📊 Exemplo de Saída Real

A IA retorna **exclusivamente JSON válido** (sem texto livre), seguindo um [schema rígido](docs/schema.json). Exemplo de um lead classificado como **🔥 Quente**:

| Campo | Valor |
|-------|-------|
| **Razão social** | Beta Distribuidora de Materiais LTDA |
| **CNPJ** | 23.456.789/0001-12 · `ATIVA` |
| **Ramo** | Comércio atacadista de materiais de construção |
| **Score** | **87 / 100** |
| **Classificação** | 🔥 **Quente** |
| **Confiança da IA** | 0.93 |
| **Próxima ação** | Contato telefônico inicial → apresentação → reunião |

<details>
<summary>📄 Ver JSON completo da resposta</summary>

```json
{
  "razao_social": "Beta Distribuidora de Materiais LTDA",
  "cnpj": "23.456.789/0001-12",
  "ramo": "Comércio atacadista de materiais de construção",
  "overall_score": 87,
  "bucket": "quente",
  "confidence": 0.93,
  "signals_positive": [
    "CNPJ ativo e regular",
    "Segmento alinhado ao setor de construção civil",
    "Website ativo com informações institucionais",
    "Boa avaliação no Google Maps",
    "Presença ativa em redes sociais"
  ],
  "signals_negative": [
    "Capital social moderado comparado a grandes distribuidores"
  ],
  "rationale": "Lead apresenta maturidade operacional, reputação online positiva e forte compatibilidade com o segmento de materiais de construção.",
  "next_actions": [
    "Contato telefônico inicial para qualificação comercial",
    "Envio de apresentação institucional",
    "Agendamento de reunião com representante comercial"
  ]
}
```

> Veja o exemplo completo em [`examples/sample-output.json`](examples/sample-output.json).

</details>

---

## 🧮 Lógica de Pontuação

O score combina **regras determinísticas** (pontuação fixa) com **análise contextual da IA**.

| Critério | Pontos | O que avalia |
|----------|:------:|--------------|
| **Regularidade Cadastral** | 25 | CNPJ ativo, natureza jurídica válida, porte definido |
| **Contato Digital** | 25 | Telefone, e-mail, site, horário, sócios identificados |
| **Estabilidade Empresarial** | 20 | Tempo de mercado + capital social |
| **Potencial Comercial** | 20 | Aderência ao ICP (construção civil) |
| **Reputação Online** | 10 | Presença e avaliações no Google Maps |
| **Total** | **100** | |

### Buckets de classificação

| Score | Classificação |
|:-----:|:-------------:|
| `80–100` | 🔥 Lead Quente |
| `60–79` | 🌤 Lead Morno |
| `0–59` | ❄ Lead Frio |

📖 Detalhamento completo em [`docs/scoring-logic.md`](docs/scoring-logic.md).

---

## 🏗 Arquitetura

O fluxo é dividido em **5 camadas independentes e modulares**:

| # | Etapa | Responsabilidade |
|:-:|-------|------------------|
| 1️⃣ | **Ingestão de Dados** | Consulta Receita Federal + Google Maps por CNPJ |
| 2️⃣ | **Validação Cadastral** | Descarta CNPJ inexistente ou inativo |
| 3️⃣ | **Deduplicação Inteligente** | Evita reprocessar CNPJ já analisado (economia de API) |
| 4️⃣ | **Enriquecimento Digital** | Scraping do website → HTML → JSON estruturado |
| 5️⃣ | **Classificação com IA** | Score 0–100 + bucket + sinais + próximas ações |

📖 Documentação detalhada em [`docs/architecture.md`](docs/architecture.md).

---

## 🧠 Estratégia de IA

O prompt foi estruturado para **previsibilidade e auditabilidade**:

- ✅ Força resposta **exclusivamente em JSON** (sem alucinação textual)
- ✅ Proíbe explicar a lógica interna do modelo
- ✅ Mantém consistência com o schema definido
- ✅ Retorna sinais de **transparência**: `signals_positive`, `signals_negative`, `missing_fields`, `rationale` e `confidence`

Esses campos permitem **auditoria posterior**, **explicabilidade do modelo** e **ajuste de pesos** no futuro.

---

## 🛠 Stack

- **n8n** — orquestração do workflow
- **API Receita Federal** — dados cadastrais (CNPJ)
- **API Google Maps** — presença digital, telefone, avaliações, website
- **Módulo HTML** — scraping e extração de conteúdo do site
- **OpenRouter** — IA via modelo open-source (custo zero)
- **JSON Schema (draft-07)** — padronização e validação da saída

---

## ▶️ Como Executar

> **Pré-requisitos:** uma instância do n8n ([cloud](https://n8n.io/cloud/) ou [self-hosted](https://docs.n8n.io/hosting/)) e chaves das APIs utilizadas.

1. **Importe o workflow**
   - No n8n: `Workflows` → `Import from File` → selecione [`flow/n8n-flow.json`](flow/n8n-flow.json).

2. **Configure as credenciais** (em `Settings → Credentials`):

   | Variável | Onde usar |
   |----------|-----------|
   | `OPENROUTER_API_KEY` | Nó de classificação por IA |
   | `GOOGLE_MAPS_API_KEY` | Nó de enriquecimento Google Maps |

   > Veja [`.env.example`](.env.example) para a lista completa.

3. **Forneça a entrada** — uma planilha/lista de CNPJs no nó de ingestão.

4. **Execute** o workflow e colete a base classificada em JSON.

---

## 📈 Resultados e Impacto

### Benefícios

- ⏱ **Redução do tempo** de qualificação manual de leads
- 🎯 **Priorização inteligente** — o time foca primeiro nos leads quentes
- 🗂 **Base estruturada e padronizada** para o comercial
- 📊 **Decisão orientada por dados**, não por intuição
- 💰 **Custo operacional mínimo** (APIs públicas + modelo gratuito)

### Métricas (estimativas ilustrativas)

> ⚠️ **Valores ilustrativos** para demonstrar o tipo de impacto medido pelo pipeline.
> Substitua pelos números reais após executar com sua própria base.

| Métrica | Valor | Como é obtida |
|---------|:-----:|---------------|
| Tempo de qualificação por lead | **~8 min → ~5 s** | Manual vs. automatizado pelo workflow |
| Chamadas de API evitadas | **proporcional aos CNPJs repetidos** | Etapa de deduplicação (cap. 3️⃣) |
| Custo de IA por lead | **~US$ 0,00** | Modelo open-source via OpenRouter |
| Cobertura de classificação | **100% dos CNPJs ativos** | Todo lead válido recebe score + bucket |
| Confiança média da IA | **0.93** *(no exemplo)* | Campo `confidence` na saída |

**Metodologia das estimativas:** o ganho de tempo compara a triagem manual (consultar CNPJ na Receita, buscar site, avaliar porte e reputação) com a execução automatizada. A economia de API vem da deduplicação, que ignora CNPJs já processados antes de qualquer nova chamada. O custo de IA é zero por usar modelo gratuito via OpenRouter.

---

## 🔮 Roadmap

- [ ] Dashboard em **Power BI** sobre a base classificada
- [ ] **Persistência** em banco relacional + histórico temporal
- [ ] **API REST própria** para consumo do score
- [ ] Integração automática com **CRM**
- [ ] Ajuste dinâmico de pesos / **aprendizado supervisionado**
- [ ] Monitoramento e **logging estruturado**

---

## 📂 Estrutura do Repositório

```
lead-scoring-b2b-n8n/
├── docs/
│   ├── architecture.md      # Arquitetura do pipeline (5 camadas)
│   ├── scoring-logic.md     # Lógica de pontuação detalhada
│   ├── json-schema.md       # Documentação do schema
│   └── schema.json          # JSON Schema (draft-07) da saída
├── examples/
│   └── sample-output.json   # Exemplo real de lead classificado
├── flow/
│   ├── n8n-flow.json        # Workflow exportado do n8n
│   ├── flow-diagram.png     # Diagrama visual do fluxo
│   └── demo.gif             # (opcional) GIF do workflow rodando
├── README.md                # Documentação (PT-BR)
└── README.en.md             # Documentation (English)
```

---

## 📜 Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](LICENSE) para mais detalhes.

---

<sub>© 2026 Rayana Santos — Desenvolvido como projeto de portfólio em automação e IA aplicada a negócios.</sub>
