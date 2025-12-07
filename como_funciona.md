# 🔍 Como Funciona o Sistema

## O Problema que Resolvi

Como trader há 8 anos, eu gastava **15 minutos** analisando cada ação:
- Abrir 5+ sites de notícias
- Checar gráficos técnicos manualmente
- Ler recomendações de analistas
- Cruzar tudo mentalmente

No day trade, isso mata produtividade. Precisava de velocidade.

## A Solução: Agentes de IA

Criei um sistema onde **3 agentes trabalham em equipe**:

```
Você digita: MSFT
     ↓
┌────────────────────────────────────┐
│     Coordenador (cérebro)          │
│  "Preciso analisar Microsoft"      │
└──────┬─────────────────────┬───────┘
       │                     │
       ▼                     ▼
┌─────────────┐      ┌──────────────┐
│ Agente Web  │      │ Agente       │
│  Search     │      │ Financeiro   │
│             │      │              │
│ Busca:      │      │ Busca:       │
│ • Notícias  │      │ • Preços     │
│ • Sentimento│      │ • Analistas  │
│   mercado   │      │ • Fundamentos│
└─────────────┘      └──────────────┘
       │                     │
       └──────┬──────────────┘
              ▼
       ┌─────────────┐
       │ IA Resume   │
       │ Tudo        │
       └─────────────┘
              ▼
       Você lê em 5 segundos
```

## Fluxo Passo a Passo

### 1️⃣ **Você Digita o Ticker**
Interface simples: um campo de texto + botão "Analisar"

### 2️⃣ **Sistema Busca Dados**
**Agente Financeiro** usa YFinance para pegar:
- Preços dos últimos 6 meses
- Recomendações de analistas (comprar/vender)
- Dados fundamentalistas (receita, lucro, P/L)

**Agente Web Search** usa DuckDuckGo para:
- Notícias recentes sobre a empresa
- Sentiment (positivo/negativo) do mercado

### 3️⃣ **IA Processa Tudo**
O modelo de IA (via Groq) lê TUDO e responde:
- "Analistas recomendam compra forte"
- "Última notícia: empresa bateu meta de receita"
- "Atenção: volume de negociação caiu 15%"

### 4️⃣ **Gráficos Aparecem**
Sistema gera automaticamente:
- **Linha do tempo**: Preço nos últimos 6 meses
- **Candlestick**: Abertura, fechamento, máxima, mínima
- **Médias Móveis**: SMA e EMA de 20 períodos
- **Volume**: Intensidade de negociação

## Tecnologias (e Por Que Escolhi)

### **Streamlit**
> Interface web sem precisar HTML/CSS

**Por quê:** Queria focar em resolver o problema, não em front-end. Com Streamlit, 10 linhas de Python = app web.

### **Phidata (Multi-Agent)**
> Framework para orquestrar agentes de IA

**Por quê:** Cada agente tem uma especialidade. É como ter 3 assistentes: um lê notícias, outro analisa números, e um terceiro coordena.

### **Groq**
> API de inferência de LLMs (usa modelos OpenAI)

**Por quê:** Grátis, rápido (importante pra real-time) e compatível com OpenAI.

### **YFinance**
> Biblioteca que puxa dados do Yahoo Finance

**Por quê:** Gratuita, completa e confiável. Dados de preços + fundamentalistas + recomendações.

### **Plotly**
> Gráficos interativos

**Por quê:** Gráficos bonitos e interativos (zoom, hover) sem esforço.

## O Que Aprendi Construindo Isso

### **Do Lado Técnico:**
- Como orquestrar múltiplos agentes de IA
- Integração de APIs (Groq, YFinance, DuckDuckGo)
- Deploy em cloud (AWS EC2)
- Cache de dados para performance

## Limitações Atuais

- **Dados**: Dependente do Yahoo Finance (grátis, mas pode ter delays)
- **Escalabilidade**: Roda bem para 1 usuário, precisa ajustes para muitos
- **Predição**: Não prevê preços futuros (ainda - é o próximo passo)

## Próximos Passos

- [ ] Adicionar modelo preditivo (LSTM/Transformer)
- [ ] Sistema de alertas
- [ ] Previsão de preços futuros
- [ ] Alterar de Nasdaq para Bovespa

---

**Em resumo:** Apliquei tecnologia moderna (IA + agentes). Não é o código mais complexo do mundo, mas **funciona**. Cumpriu o fim didático.

Se tiver dúvidas técnicas ou quiser contribuir: biasandrade@gmail.com
