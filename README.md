# Prompt2C · Biblioteca Colaborativa de Prompts

> Uma biblioteca viva, construída pela equipa Get2C — para partilhar, votar e descobrir os prompts que produzem resultados de excelência com IA.

🔗 **[Abrir Prompt2C](https://tech2c-devteam.github.io/prompt2c/)**

---

## O que é o Prompt2C

O Prompt2C é uma ferramenta colaborativa interna que permite à equipa Get2C construir, partilhar e avaliar prompts de IA de alta qualidade. Em vez de cada pessoa reinventar a roda, os melhores prompts ficam centralizados, votados e acessíveis a todos.

**A premissa é simples:** quanto melhor cada um de nós dominar o uso da IA, melhor o trabalho que entregamos aos clientes.

---

## Funcionalidades

- **Biblioteca de prompts** organizada por categoria de tarefa (Propostas, Relatórios, Dados, Excel, Comunicação, Apresentações) e por equipa (Financeiro, Contabilidade, Comercial, Marketing, RH) e por técnica
- **Prompts em português**, ancorados no contexto Get2C (ambiente e sustentabilidade), com os identificadores de norma em inglês
- **Sistema de votação** (upvote/downvote) — os melhores prompts sobem ao topo
- **Avaliação por estrelas** (1 a 5) para medir qualidade do output
- **Leaderboard** em tempo real dos prompts mais votados pela equipa
- **Submissão de novos prompts** com exemplo de resultado e link externo
- **Secção pedagógica** sobre as três técnicas principais: One-Shot, Few-Shot e Chain-of-Thought
- **Modo claro e escuro** com as cores da marca 2C
- **Base de dados partilhada** via Supabase — toda a equipa vê os mesmos dados em tempo real
- **Exportação de backup** em JSON a qualquer momento

---

## Como usar

### Usar um prompt existente

1. Navega pela biblioteca ou usa a pesquisa
2. Clica em **"Ver prompt"** para expandir o conteúdo
3. Clica em **"Copiar prompt"** para copiar para a área de transferência
4. Substitui os campos `[ASSIM]` pelo contexto real do teu projecto
5. Cola no Claude, Cowork ou outra ferramenta de IA

### Votar e avaliar

- **▲ Upvote** — o prompt funcionou bem, recomendo à equipa
- **▼ Downvote** — o prompt não produziu bons resultados
- **★ Estrelas** — avalia a qualidade do output de 1 a 5

### Submeter um novo prompt

1. Clica no botão **"+ Submeter Prompt"** (canto inferior direito)
2. Preenche o formulário — título, categoria, técnica, e o prompt completo
3. Adiciona opcionalmente um excerto do resultado ou link para documento
4. Clica **"Publicar"**

> ⚠️ Não incluas nomes de clientes reais ou dados confidenciais. Usa `[CLIENTE]`, `[PROJECTO]` como placeholders.

---

## Técnicas de prompting

| Técnica | Quando usar |
|---------|-------------|
| **One-Shot** | Tarefas com formato universal, velocidade > estilo exacto |
| **Few-Shot** | Replicar estilo da empresa, estruturas técnicas específicas |
| **Chain-of-Thought** | Análises de conformidade, decisões com múltiplos critérios |

---

## Categorias disponíveis

As categorias cruzam duas dimensões: **tipo de tarefa** (as 6 primeiras) e **equipa** (as 5 últimas).

| Categoria | Exemplos de uso |
|-----------|----------------|
| **Propostas** | Resumos executivos, Scope of Work, justificação de fees |
| **Apresentações** | Estrutura de slides, narrativa, argumentação para steering committee |
| **Relatórios** | Sumário Não Técnico, matrizes de significância, conformidade regulatória |
| **Dados** | Interpretação de monitorização, tabelas de compliance, diagnóstico de anomalias |
| **Excel** | Registos de monitorização, cálculos BNG, trackers de fees |
| **Comunicação** | Emails de seguimento, resposta a objecções, preparação de reuniões difíceis |
| **Financeiro** | Análise de desvios, fecho mensal, viabilidade de investimento |
| **Contabilidade** | Enquadramento contabilístico, justificação de saldos, tratamento de operações complexas |
| **Comercial** | Prospeção, resposta a objeções, preparação de negociação |
| **Marketing** | Posts LinkedIn, títulos no tom da marca, diagnóstico de funil |
| **RH** | Descrição de funções, feedback estruturado, análise de casos de pessoas |

---

## Arquitectura técnica

```
prompt2c/
├── index.html          # Aplicação completa (HTML + CSS + JS inline)
└── README.md           # Este ficheiro
```

### Stack

| Componente | Tecnologia | Motivo |
|-----------|-----------|--------|
| Frontend | HTML + CSS + JS vanilla | Zero dependências, abre em qualquer browser |
| Base de dados | Supabase (PostgreSQL) | Tier gratuito, REST API nativa, RLS policies |
| Hosting | GitHub Pages | Gratuito, HTTPS automático, deploy por git push |
| Fonts | Google Fonts (Fraunces + Inter + JetBrains Mono) | Identidade visual profissional |

### Tabelas Supabase

```sql
prompts    — id, title, author, description, category, type,
             score, stars, star_count, prompt, output, link, created_at

activity   — id, icon, text, created_at
```

### Segurança

- Chave utilizada: `anon public` (desenhada para ser exposta em clientes)
- Row Level Security (RLS) activo em todas as tabelas
- Políticas: leitura e escrita pública (adequado para ferramenta interna)
- Sem autenticação de utilizador (decisão consciente para reduzir fricção numa equipa pequena)

---

## Como actualizar a ferramenta

Qualquer alteração ao `index.html` é publicada automaticamente no GitHub Pages em 2-3 minutos.

**Fluxo de actualização:**

1. Abre o ficheiro `index.html` no repositório
2. Clica no ícone de edição (✏️)
3. Faz as alterações
4. Clica **"Commit changes"**
5. Aguarda 2-3 minutos → página actualizada para todos

---

## Roadmap

### v1.0 — Lançamento (actual)
- [x] Biblioteca com 36 prompts de arranque em português (21 consultoria + 15 equipas: Financeiro, Contabilidade, Comercial, Marketing, RH)
- [x] Sistema de votação e rating
- [x] Formulário de submissão com exemplo de resultado
- [x] Secção pedagógica One-Shot / Few-Shot / Chain-of-Thought
- [x] Modal de boas-vindas
- [x] Dark/Light mode
- [x] Sincronização Supabase em tempo real
- [x] Backup JSON

### v1.1 — Próxima iteração
- [ ] Upload de imagem (screenshot do output) via Supabase Storage
- [ ] Botão "Testar prompt" com integração directa Claude API

### v2.0 — Expansão
- [~] Cobertura por equipa — **feito parcialmente (2026-06-16)**: criadas categorias Financeiro, Contabilidade, Comercial, Marketing e RH, com prompts de arranque dedicados. Falta a separação total em workspaces independentes (filtragem/permissões por equipa).
- [ ] Versioning de prompts (histórico de edições)
- [ ] Analytics de uso (prompts mais copiados)
- [ ] Arquivo automático de prompts com score negativo

---

## Workspace actual

| Workspace | Estado | URL |
|-----------|--------|-----|
| Get2C · Consultoria | ✅ Activo | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |
| Get2C · RH | 🟡 Coberto por categoria | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |
| Get2C · Financeiro | 🟡 Coberto por categoria | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |
| Get2C · Marketing | 🟡 Coberto por categoria | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |
| Get2C · Comercial | 🟡 Coberto por categoria | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |
| Get2C · Contabilidade | 🟡 Coberto por categoria | [prompt2c](https://tech2c-devteam.github.io/prompt2c/) |

---

## Contribuir

A biblioteca cresce com a equipa. As regras são simples:

1. **Só partilhas prompts que já testaste** num caso real
2. **Usa placeholders** `[ASSIM]` para campos variáveis
3. **Sem dados de clientes** — usa `[CLIENTE]`, `[PROJECTO]`
4. **Vota honestamente** — um downvote honesto vale mais que um upvote de cortesia

---

## Responsável

Iniciativa da área de AI da **Get2C** · Grupo 2C  
Contacto interno: Vanessa Ávila

---

*Prompt2C · v1.3 · Get2C · actualizado a 2026-06-16*
