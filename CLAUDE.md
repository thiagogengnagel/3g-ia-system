# 3G IA System — Sistema operacional do negócio

Sua empresa roda em cima desse arquivo. Aqui ficam as regras de operação
do 3G IA System — como o Claude lê o contexto, aprende com correções, mantém
tudo atualizado e cria skills novas conforme a operação evolui.

Esse arquivo é editável. Quando o `/instalar` rodar, ele complementa o
final dessa página com as regras específicas do seu negócio.

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (quando existirem
e estiverem preenchidos):

1. `_memoria/empresa.md` — quem é o usuário, o que faz, como funciona o negócio
2. `_memoria/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_memoria/estrategia.md` — foco atual, prioridades, prazos

Usar essas informações como base pra qualquer resposta ou decisão. Ao
sugerir prioridades, formatos ou abordagens, considerar o foco atual
descrito em `estrategia.md`.

Pra qualquer tarefa visual (carrossel, post, landing page), consultar
`identidade/design-guide.md` como referência de estilo.

Não é necessário listar o que foi lido nem confirmar a leitura. Apenas
usar o contexto naturalmente.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe skill relevante
em `.claude/skills/`. Se encontrar, seguir as instruções da skill. Se
não encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa que não tinha skill mas parece repetível (o
usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o
padrão de repetição for claro.

---

## Calibrar ajuda pelo nível de IA do usuário

`_memoria/preferencias.md` guarda o nível de experiência com IA que a
pessoa informou no `/instalar` (Leigo, Iniciante ou Avançado). Usar isso
pra decidir quanto orientar ao final de cada tarefa ou skill executada,
não só no `/instalar`:

- **Leigo** — terminar toda resposta relevante com um bloco "Próximos
  passos" numerado e concreto: o que fazer agora, se vale abrir um chat
  novo (e com qual pergunta), qual comando ou skill rodar em seguida.
  Não assumir nenhum conhecimento prévio de terminal, Git, VS Code ou
  dos conceitos de IA — explicar em linguagem simples, sem jargão
- **Iniciante** — terminar com uma sugestão breve de próximo passo
  (comando ou skill), sem detalhar operação básica de VS Code ou terminal
- **Avançado** — não adicionar "próximos passos" por padrão, só quando a
  pessoa pedir

Se `_memoria/preferencias.md` ainda não tiver esse campo preenchido
(sistema instalado antes dessa regra existir), perguntar uma vez qual
nível combina melhor e salvar a resposta lá.

**Recalibrar a cada 15 dias:** o campo guarda também uma "Última
calibração" (data). No início de toda conversa, comparar essa data
com a de hoje. Se tiverem passado 15 dias ou mais desde a última
calibração, perguntar — uma vez por conversa, sem travar o que a
pessoa veio fazer, pode ir junto da resposta normal:

> "Faz [X] dias desde que calibramos teu nível de IA como [nível
> atual]. Você sente que evoluiu e quer subir de nível, ou ainda se
> sente no mesmo patamar?"

Depois da resposta, atualizar `_memoria/preferencias.md`: o nível (se
mudou) e a "Última calibração" pra data de hoje — independente de ter
mudado de nível ou confirmado o mesmo. Isso reinicia a contagem dos
próximos 15 dias. Se a pessoa não responder ou desviar, não insistir
na mesma conversa; tentar de novo na próxima.

Se o campo "Última calibração" não existir (preferencias.md de antes
dessa regra), não perguntar na hora — só registrar a data de hoje
como ponto de partida e perguntar dali a 15 dias.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma
instrução que parece permanente (frases como "na verdade é assim", "não
faça mais isso", "prefiro assim", "sempre que...", "evita...", "da
próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (clientes, serviços, mercado) → `_memoria/empresa.md`
- **Sobre preferências e estilo** (tom de voz, formato, o que evitar) → `_memoria/preferencias.md`
- **Sobre prioridades e foco** (projetos, metas, prazos) → `_memoria/estrategia.md`
- **Regra de comportamento nessa pasta** → próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro.
Confirmar mostrando a linha adicionada.

Não perguntar se a correção for óbvia de contexto imediato (ex: "na
verdade o arquivo se chama X"). Só perguntar quando a informação tiver
valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante (cliente novo, skill
nova, mudança de foco, processo novo, ferramenta instalada, estrutura
alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize a memória?"

Se sim, identificar o que atualizar:

- **Cliente, serviço, ferramenta, equipe** → `_memoria/empresa.md`
- **Mudança de prioridade ou foco** → `_memoria/estrategia.md`
- **Tom ou estilo** → `_memoria/preferencias.md`
- **Pasta, regra de organização, skill criada** → `CLAUDE.md`
- **Visual (cores, fontes, logo)** → `identidade/design-guide.md`

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo
inteiro, só adicionar ou editar a linha relevante.

**Quando NÃO perguntar:**
- Tarefas pontuais sem impacto no contexto (escrever um email avulso, criar um post)
- Perguntas simples ou conversas sem ação
- Mudanças já salvas pelo bloco "Aprender com correções"

**Dica:** rode `/atualizar` pra uma varredura completa quando houver dúvida.

---

## Criação de skills

Quando o usuário pedir skill nova:

1. Verificar se existe template relevante em `templates/skills/`. Se
   existir, usar como base e adaptar pro contexto
2. Perguntar se é específica desse projeto ou útil em qualquer:
   - Específica → `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Universal → `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_memoria/empresa.md` e `_memoria/preferencias.md` pra calibrar
   o conteúdo da skill ao contexto do negócio
4. Se a skill precisar de arquivos de apoio (templates, exemplos),
   criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code

---

# 3G Aceleradora

> Perfil: agência / consultoria — equipe pequena (2 pessoas) entregando
> mentoria, consultoria e implementação de IA pra múltiplos clientes.

## O que é esse workspace

Operação da 3G Aceleradora. Aqui ficam clientes, propostas, conteúdo e
entregas da mentoria de aceleração de negócios.

**Estrutura de pastas:**
- `_memoria/` — quem é a 3G Aceleradora, como falamos, foco atual
- `identidade/` — marca da 3G Aceleradora (logo, cores, fontes)
- `dados/` — arquivos a analisar (relatórios de cliente, exports de ads)
- `marketing/` — conteúdo institucional da própria 3G Aceleradora
- `saidas/` — documentos pontuais, análises
- `templates/` — modelos reutilizáveis
- `clientes/` — criar uma subpasta por cliente conforme forem entrando (`clientes/<Nome>/`)
- `propostas/` — criar conforme propostas forem sendo montadas (`propostas/<cliente>-<data>.html`)

## Sobre a agência

Aceleradora digital focada em performance para o negócio do cliente —
implementamos conteúdo, marketing e IA. Atendemos empresários que faturam
R$ 30-50k/mês, com 1-4 colaboradores, sofrendo com estagnação, falta de
funil e dependência de indicação.

Serviços principais:
- Mentoria individual (R$ 5.000, 90 dias, aula semanal)
- Implementação do 3G IA System em outras empresas (a partir de R$ 1.500)
- Prestação de serviço de tráfego pago (a partir de R$ 1.500/mês)

Time: 2 pessoas — Thiago (IA e marketing) e sua irmã/sócia (conteúdo e
marketing).

## O que mais produzimos aqui

- Propostas comerciais pra novos clientes
- Conteúdo pra redes (Método EU)
- Campanhas de tráfego pago (Meta Ads e Google Ads)
- Diagnósticos e relatórios de performance de campanha

## Tom de voz

Direto e informal — fala do jeito que pensa, sem forçar textos
"engajados" pra não soar robótico. Evitar vícios de linguagem como
"tipo", "então", "hmmm" e jargão de guru.

## Regras do sistema

- Cliente novo → criar pasta `clientes/<Nome>/` com briefing, estratégia
  e subpastas conforme as entregas contratadas
- Proposta nova → `propostas/<cliente>-<data>.html` antes de fechar
- Casos de sucesso ficam em `clientes/<Nome>/caso.md` (reuso em pitches)

## Ferramentas conectadas

- [ ] Notion
- [ ] Gmail
- [ ] Google Calendar
- [ ] Canva
- [x] Meta Ads
- [x] Google Ads

*(Marcar conforme for instalando os MCPs)*
