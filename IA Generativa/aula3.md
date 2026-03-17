# ✍️ Prompt Engineering
### A arte de conversar com IAs de forma eficiente

---

## 1. O que é Prompt Engineering?

**Prompt** é qualquer texto que você envia para um LLM como entrada.  
**Prompt Engineering** é a habilidade de **escrever prompts de forma estratégica** para obter respostas melhores, mais precisas e mais úteis.

> 💡 **Analogia:** Imagine que o LLM é um funcionário extremamente talentoso, mas que segue instruções **ao pé da letra**. Se você der instruções vagas, ele vai adivinhar o que você quer — e pode errar. Se você for claro e detalhado, ele entrega exatamente o que precisa.

---

## 2. Anatomia de um Prompt 🔬

Um prompt bem construído pode ter até **quatro componentes**:

```
┌─────────────────────────────────────────────────────┐
│  🎭 PAPEL       → Quem o modelo deve ser?           │
│  📋 CONTEXTO    → Qual é a situação?                │
│  📝 INSTRUÇÃO   → O que ele deve fazer?             │
│  📐 FORMATO     → Como deve responder?              │
└─────────────────────────────────────────────────────┘
```

**Exemplo completo:**

```
🎭 Você é um professor universitário de economia.
📋 Estou escrevendo um artigo sobre inflação para um público leigo.
📝 Explique o que é inflação e por que ela ocorre.
📐 Use linguagem simples, máximo 3 parágrafos, sem jargões técnicos.
```

---

## 3. Prompts Ruins vs. Prompts Bons ⚡

### ❌ Prompt vago

```
"Me fala sobre machine learning."
```
O modelo vai responder qualquer coisa — pode ser muito longo, muito técnico, ou fora do que você precisava.

---

### ✅ Prompt bem estruturado

```
"Explique o conceito de machine learning para um estudante do ensino médio,
usando uma analogia do cotidiano. Responda em até 5 linhas."
```

A diferença? **Contexto + audiência + formato + limite.**

---

## 4. Técnicas de Prompt Engineering 🛠️

---

### 4.1 Zero-Shot Prompting

O modelo responde **sem nenhum exemplo** — apenas com a instrução.

```
Prompt:
"Classifique o sentimento da frase abaixo como positivo, negativo ou neutro:
'O produto chegou atrasado, mas a qualidade superou minhas expectativas.'"

Resposta:
Positivo
```

> ✅ Funciona bem para tarefas simples e diretas.

---

### 4.2 Few-Shot Prompting 🎯

Você fornece **alguns exemplos** antes da tarefa real, ensinando o padrão desejado.

```
Prompt:
"Classifique os sentimentos:

Frase: 'Adorei o atendimento!'       → Positivo
Frase: 'O prazo foi péssimo.'        → Negativo
Frase: 'O produto foi entregue.'     → Neutro

Frase: 'Achei caro, mas valeu muito a pena.' → ?"

Resposta:
Positivo
```

> ✅ Muito útil quando você quer um **formato específico** na resposta.

---

### 4.3 Chain-of-Thought (CoT) 🧠

Você pede ao modelo para **pensar passo a passo** antes de responder. Isso melhora muito o raciocínio em problemas complexos.

```
Prompt (sem CoT):
"Se tenho 23 maçãs e dou 1/3 para minha amiga, quantas ficam?"

Resposta:
"15" ❌ (pode errar)
```

```
Prompt (com CoT):
"Se tenho 23 maçãs e dou 1/3 para minha amiga, quantas ficam?
Pense passo a passo antes de responder."

Resposta:
"1/3 de 23 = 7,67 ≈ 7 maçãs entregues.
23 - 7 = 16 maçãs restantes." ✅
```

> 💡 A simples adição de **"pense passo a passo"** pode aumentar drasticamente a precisão em problemas lógicos e matemáticos.

---

### 4.4 Role Prompting 🎭

Você atribui um **papel ou persona** ao modelo para ajustar o tom e o nível de expertise da resposta.

```
"Você é um médico cardiologista experiente. Explique o que é pressão arterial
para um paciente de 70 anos sem conhecimento médico."
```

vs.

```
"Você é um médico cardiologista experiente. Explique o que é pressão arterial
para um colega residente de medicina."
```

> A mesma pergunta → **duas respostas completamente diferentes** em tom e profundidade.

---

### 4.5 Prompt com Restrições 🚧

Adicionar restrições **aumenta o controle** sobre a saída.

| Tipo de restrição | Exemplo |
|---|---|
| 📏 Tamanho | "Responda em no máximo 100 palavras" |
| 🗂️ Formato | "Responda em formato de tabela markdown" |
| 🚫 Exclusão | "Não use jargões técnicos" |
| 🎯 Foco | "Foque apenas nos aspectos econômicos" |
| 🌐 Idioma | "Responda em inglês formal" |

---

### 4.6 Prompt Iterativo 🔄

Raramente o primeiro prompt é perfeito. O processo real é uma **conversa iterativa**:

```
1ª tentativa:  "Escreva um e-mail de vendas."
               → muito genérico

2ª tentativa:  "Reescreva, mas torne o tom mais urgente e adicione um CTA claro."
               → melhorou

3ª tentativa:  "Agora reduza para 5 linhas e adicione o nome do produto: 'ProPlan'."
               → ótimo! ✅
```

---

### 4.7 Self-Consistency 🔍

Para respostas importantes, peça ao modelo para **verificar a própria resposta**:

```
"Resolva o problema abaixo. Depois, revise sua resposta e corrija
qualquer erro antes de apresentar o resultado final."
```

---

## 5. Erros Comuns no Prompt Engineering 🚨

| ❌ Erro | ✅ Solução |
|--------|-----------|
| Ser vago ("me fala sobre X") | Especificar audiência, formato e objetivo |
| Pedir muitas coisas de uma vez | Dividir em prompts menores |
| Não dar contexto | Explicar a situação antes da pergunta |
| Aceitar a primeira resposta | Iterar e refinar |
| Perguntas com viés ("não é verdade que X?") | Perguntas neutras e abertas |

---

## 6. Engenharia de Sistema vs. Usuário 🏗️

Em aplicações reais (APIs, apps), existem dois tipos de prompt:

```
┌──────────────────────────────────────────────────────┐
│  SYSTEM PROMPT (invisível ao usuário final)          │
│  "Você é um assistente de suporte da empresa XYZ.    │
│   Responda sempre em português, seja cordial e        │
│   nunca discuta tópicos fora do produto."             │
├──────────────────────────────────────────────────────┤
│  USER PROMPT (digitado pelo usuário)                 │
│  "Como faço para cancelar minha assinatura?"         │
└──────────────────────────────────────────────────────┘
```

> 🔐 O System Prompt é uma camada de controle que **define o comportamento base** do modelo em toda a aplicação.

---

## 7. Exemplo Completo: Do Zero ao Prompt Ideal 🏆

**Objetivo:** Gerar um resumo executivo de uma reunião.

### Versão 1 — Ruim ❌
```
"Resuma essa reunião."
```

### Versão 2 — Melhor ✅
```
"Resuma os pontos principais da reunião abaixo."
[texto da reunião]
```

### Versão 3 — Ótima 🏆
```
"Você é um assistente executivo profissional.

Abaixo está a transcrição de uma reunião de negócios.
Seu trabalho é criar um resumo executivo claro e objetivo.

O resumo deve conter:
- ✅ Decisões tomadas
- 📋 Próximos passos com responsáveis
- ⚠️ Pontos em aberto / riscos identificados

Formato: tópicos em bullet points. Máximo de 200 palavras. Português formal.

[TRANSCRIÇÃO]
...
```

---

## 8. Prompt Engineering para Código 💻

LLMs são ótimos para programação — mas o prompt faz toda diferença.

### ❌ Prompt fraco
```
"Escreva um código Python para analisar dados."
```

### ✅ Prompt forte
```
"Escreva uma função Python chamada `analisar_vendas` que:
- Receba um DataFrame do pandas com colunas: 'data', 'produto', 'valor'
- Retorne o produto mais vendido por mês
- Inclua tratamento de erros para colunas ausentes
- Adicione docstring e comentários em português"
```

---

## 9. O Futuro: Prompt → Agentes 🤖

O Prompt Engineering está evoluindo para além de perguntas e respostas simples.

```
Prompt simples:
"Qual o clima hoje em SP?" → 1 resposta

Agente com ferramentas:
"Organize minha semana considerando as reuniões do calendário,
o clima de SP e meus projetos no Jira."
→ O modelo usa ferramentas, consulta APIs, raciocina em múltiplos passos
e entrega um plano completo. 🚀
```

---

## 10. 📋 Checklist do Prompt Perfeito

Antes de enviar seu prompt, verifique:

- [ ] 🎯 O objetivo está claro?
- [ ] 👥 A audiência/persona está definida?
- [ ] 📐 O formato da resposta está especificado?
- [ ] 📏 Há limite de tamanho ou estilo?
- [ ] 💡 Usei exemplos quando necessário? (few-shot)
- [ ] 🧠 Pedi raciocínio passo a passo para problemas complexos?
- [ ] 🔄 Estou disposto a iterar e refinar?

---

## 📚 Referências para Aprofundar

- [Prompt Engineering Guide](https://www.promptingguide.ai/pt) — guia completo em português
- [Learn Prompting](https://learnprompting.org/) — curso gratuito e interativo
- [OpenAI Prompt Engineering](https://platform.openai.com/docs/guides/prompt-engineering) — guia oficial da OpenAI
- [Anthropic Claude Prompting Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) — guia oficial do Claude

---

> ✍️ *"A qualidade da sua pergunta determina a qualidade da resposta."*  
> — Princípio fundamental do Prompt Engineering
