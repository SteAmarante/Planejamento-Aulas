# 🧠 Modelos de Linguagem (LLMs)


---

## 1. O que é um Modelo de Linguagem?

Imagine que você está digitando uma mensagem no celular e ele **sugere a próxima palavra** automaticamente. Isso é, na essência, o que um modelo de linguagem faz — ele aprende padrões de texto e **prevê o que vem a seguir**.

> 💡 **Definição simples:** Um Modelo de Linguagem é um sistema treinado para entender e gerar texto, prevendo qual palavra (ou token) é mais provável de aparecer em seguida, dado um contexto.

---

## 2. O que é um "Token"?

LLMs não leem palavras inteiras — eles leem **tokens**, que são pedaços de texto.

| Texto | Tokens |
|-------|--------|
| `cachorro` | `cach` + `orro` |
| `inteligência` | `intelig` + `ência` |
| `AI` | `AI` |

> 🔢 Em média, 1 palavra ≈ 1,3 tokens em português.

---

## 3. Como um LLM aprende?

O treinamento acontece em **duas grandes fases**:

### Fase 1 — Pré-treinamento (aprender o idioma)

O modelo lê **bilhões de textos** da internet, livros, artigos etc. Ele não é ensinado explicitamente — ele aprende por tentativa e erro:

```
Entrada:  "O céu é de cor ___"
Chute:    "verde"
Correto:  "azul"
→ Ajusta os pesos internos para acertar mais da próxima vez
```

Isso é feito **trilhões de vezes**, ajustando milhões (ou bilhões) de parâmetros.

### Fase 2 — Fine-tuning com feedback humano (RLHF)

Após o pré-treinamento, o modelo é refinado para ser **útil, seguro e honesto**, usando feedback de avaliadores humanos.

---

## 4. A Arquitetura Transformer 🔧

Todos os LLMs modernos (GPT, Claude, Gemini, LLaMA...) são baseados na arquitetura **Transformer**, criada pelo Google em 2017.

O componente mais importante é o **mecanismo de atenção (Attention)**:

> 🎯 **Atenção** permite que o modelo saiba *quais palavras do contexto são mais relevantes* para entender a palavra atual.

**Exemplo:**
```
"O banco estava cheio de pessoas esperando para sacar dinheiro."
       ↑
  Qual "banco"? → financeiro? de praça?
```
O mecanismo de atenção conecta "banco" com "sacar dinheiro" e resolve a ambiguidade.

---

## 5. O que são "Parâmetros"?

Parâmetros são os **"neurônios"** do modelo — números ajustados durante o treinamento que armazenam o conhecimento aprendido.

| Modelo | Parâmetros (aprox.) |
|--------|---------------------|
| GPT-2 (2019) | 1,5 bilhão |
| GPT-3 (2020) | 175 bilhões |
| LLaMA 3 (2024) | até 405 bilhões |
| Claude 3 Opus | não divulgado |

> 📌 Mais parâmetros ≠ sempre melhor. Eficiência de treinamento e qualidade dos dados importam muito.

---

## 6. Como o Modelo Gera Texto?

A geração de texto é um processo **iterativo e probabilístico**:

```
Prompt: "A capital do Brasil é"

Distribuição de probabilidade:
  "Brasília"  → 94%  ✅ escolhido
  "São Paulo" →  4%
  "Rio"       →  2%
```

Esse processo se repete **token por token** até o modelo decidir parar.

### Temperatura 🌡️

A **temperatura** controla a criatividade da resposta:

- **Temperatura baixa (0.1)** → respostas mais previsíveis e precisas
- **Temperatura alta (1.5)** → respostas mais criativas e variadas (mas podem ser menos coerentes)

---

## 7. Janela de Contexto

A **janela de contexto** é a quantidade de texto que o modelo consegue "ver" de uma vez — como sua memória de curto prazo.

```
┌─────────────────────────────────────────┐
│  Tudo que o modelo consegue "enxergar"  │
│  ← — — — — janela de contexto — — — → │
│  [conversa passada] [documento] [prompt]│
└─────────────────────────────────────────┘
```

| Modelo | Contexto |
|--------|----------|
| GPT-3.5 | 16k tokens |
| GPT-4o | 128k tokens |
| Claude 3.5 | 200k tokens |
| Gemini 1.5 Pro | 1 milhão de tokens |

---

## 8. Limitações dos LLMs ⚠️

| Limitação | Descrição |
|-----------|-----------|
| 🔮 **Alucinações** | O modelo pode inventar fatos com confiança |
| 📅 **Conhecimento desatualizado** | Dados têm uma data de corte |
| 🧮 **Aritmética fraca** | LLMs não são calculadoras — erram contas |
| 🔁 **Sem memória persistente** | Cada conversa começa do zero |
| 🌀 **Viés** | Reflete os vieses presentes nos dados de treinamento |

---

## 9. Aplicações Práticas

```
📝 Geração de texto       → redação, resumos, tradução
💻 Código                 → GitHub Copilot, geração e revisão de código
🔍 Busca semântica        → encontrar documentos por significado
🤖 Assistentes            → ChatGPT, Claude, Gemini
📊 Análise de dados       → interpretar tabelas e relatórios em linguagem natural
🎓 Educação               → tutores personalizados
```

---

## 10. Resumo Visual

```
         TEXTO DE ENTRADA (Prompt)
                  ↓
         Tokenização
                  ↓
    ┌─────────────────────────┐
    │     TRANSFORMER         │
    │  (camadas de atenção)   │
    │  Entende o contexto     │
    └─────────────────────────┘
                  ↓
    Distribuição de probabilidade
                  ↓
         Próximo token gerado
                  ↓
    (repete até o fim da resposta)
                  ↓
         TEXTO DE SAÍDA
```

---

## 📚 Referências para aprofundar

- [Attention Is All You Need](https://arxiv.org/abs/1706.03762) — artigo original do Transformer (Vaswani et al., 2017)
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) — explicação visual excelente
- [Andrej Karpathy — Let's build GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY) — do zero em Python
- [Sebastian Raschka — LLMs from scratch](https://github.com/rasbt/LLMs-from-scratch)


