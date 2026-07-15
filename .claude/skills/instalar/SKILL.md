---
name: instalar
description: >
  Instala o 3G IA System no negócio do usuário. Entrevista sobre nível de experiência com IA,
  empresa, tom de voz, foco atual e identidade visual, e preenche `_memoria/empresa.md`,
  `_memoria/preferencias.md`, `_memoria/estrategia.md`, `identidade/design-guide.md` e adapta
  o `CLAUDE.md` conforme o perfil. Use quando o usuário acabou de clonar o repositório e quer
  instalar o sistema, ou quando pedir explicitamente "rodar /instalar", "instalar o 3G IA System",
  "primeiro setup".
---

# /instalar — Instalação inicial do 3G IA System

Esse é o primeiro comando que o usuário roda depois de clonar o repositório — normalmente numa call de implantação com a 3G, mas funciona igual se ele rodar sozinho. Não pode falhar e não pode soar burocrático. Trata como conversa de descoberta — pergunta uma coisa por vez, escuta de verdade, não enfileira tudo.

O objetivo é duplo: o sistema sair daqui sabendo quem é a empresa e como ela fala, E o empresário sair com um **mini-diagnóstico 3G** do negócio — gargalo, números e canais mapeados. É a primeira entrega de valor, não um formulário.

## Pré-checagem

### 1. Nome da pasta

Conferir o nome da pasta atual (`basename "$(pwd)"`). Se for `3g-ia-system`, `3G IA System`, `3g-ia-system-main` ou variação genérica:

> "Notei que a pasta atual ainda tem nome genérico ('<nome-atual>'). O ideal é a pasta ter o nome do seu negócio, não '3G IA System'. Quando terminarmos o setup, te lembro de renomear (é rápido — fechar VS Code, renomear a pasta no Finder/Explorer, abrir de novo). Bora seguir?"

Registrar mentalmente o nome atual pra usar na Fase 5.

### 2. Arquivos de contexto

Conferir se algum arquivo de memória já está preenchido (não é placeholder):
- `_memoria/empresa.md`
- `_memoria/preferencias.md`
- `_memoria/estrategia.md`
- `identidade/design-guide.md`

Se algum já tiver conteúdo real, perguntar:
> "Já tem algum contexto preenchido aqui. Quer que eu sobrescreva (recomeçar do zero) ou complemente o que falta?"

Se for setup limpo, seguir direto.

---

## Fase 0 — Nível de experiência com IA

Antes de qualquer outra pergunta:

> "Antes de começar, uma pergunta importante: qual é o teu nível de experiência com inteligência artificial hoje? Isso me ajuda a calibrar o quanto de ajuda te dar no dia a dia, sem te sobrecarregar nem te deixar perdido.
>
> 1. **Leigo** — essa seria minha primeira vez usando uma ferramenta de IA assim
> 2. **Iniciante** — já uso ChatGPT ou IA no dia a dia, mas nunca mexi em terminal, Git ou VS Code
> 3. **Avançado** — sou confortável com tecnologia, já uso Claude Code ou ferramenta parecida"

Registrar a resposta pra usar na Fase 3. Se a pessoa disser "leigo", adaptar o próprio tom do resto da entrevista: explicar cada pergunta em linguagem simples, sem jargão técnico, e ir com calma — essa calibração vale a partir de agora, não só depois do setup.

---

## Fase 1 — Escolha do perfil

Perguntar qual perfil mais combina com o negócio:

1. **Solopreneur / criador solo** — uma pessoa só, mistura de marca pessoal e negócio
2. **Freelancer** — atende clientes, organiza por projeto/cliente
3. **Agência / consultoria** — equipe pequena entregando pra vários clientes
4. **Empresa** — empresa estabelecida com setores (marketing, comercial, financeiro, etc.)

A resposta determina qual template de `CLAUDE.md` aplicar (ver `templates/perfis/`).

---

## Fase 2 — Entrevista

Fazer essas perguntas em ordem, esperando a resposta de cada uma antes de seguir. Se vier resposta vaga, repetir uma vez pedindo concretude. Não insistir mais que isso — registrar o que vier.

**Sobre o negócio:**
1. "Como você chama o que você faz? (nome da empresa, ou seu nome se for marca pessoal)"
2. "O que sua empresa entrega, em uma frase do jeito que você falaria pro vizinho?"
3. "Quem te paga? (perfil de cliente real — descreve em uma ou duas frases, sem persona genérica)"
4. "Você toca sozinho ou tem equipe? Se tem, quantos e cada um fazendo o quê?"

**Sobre voz:**
5. "Me cola um exemplo da tua escrita — uma legenda do Insta, um email pra cliente, qualquer coisa real e recente. Assim eu calibro o jeito de escrever sem precisar adivinhar."
6. "O que te dá ranço quando alguém escreve assim? (ex: 'vamos juntos!', emoji em email formal, 'caro cliente', jargão de guru, 'alavancar', 'sinergia')"

**Diagnóstico 3G (números e canais):**
7. "Quanto o negócio fatura por mês hoje, e onde você quer chegar? (número + prazo — ex: 'R$ 40k, quero R$ 70k em 6 meses')"
8. "Qual o ticket médio? (quanto um cliente paga, em média — à vista, recorrência ou projeto)"
9. "Como as vendas chegam hoje? (indicação, Instagram, anúncio, prospecção — e o que você já tentou que não funcionou)"

**Sobre foco:**
10. "Qual o gargalo do teu negócio hoje? O que tá segurando ele de crescer?"
11. "Se eu pudesse tirar UMA coisa que você repete toda semana das tuas costas, qual seria?"

**Sobre identidade visual:**
12. "Tem identidade visual definida ou tá no zero? Se tem, me passa as cores principais e a fonte."
13. "Tem logo? Se sim, joga o arquivo em `identidade/logo.png` (ou `.svg`) e me confirma."

---

## Fase 3 — Preenchimento dos arquivos

### `_memoria/empresa.md`
Preencher com base nas perguntas 1-4. Manter formato simples — nome, o que faz, perfil de cliente, equipe.

### `_memoria/preferencias.md`
Preencher com base nas perguntas 5-6 e na Fase 0. Estrutura:
- **Tom de voz:** derivar do exemplo de escrita real da pergunta 5 (descrever em 2-3 frases o jeito de escrever, com referência ao exemplo)
- **O que evitar:** lista direta da resposta 6
- **Estilo geral:** síntese do que combina e o que destoa
- **Nível de experiência com IA:** o nível escolhido na Fase 0 (Leigo/Iniciante/Avançado) mais a data de hoje como "Última calibração". Formato:
  ```
  ## Nível de experiência com IA

  **Nível:** [Leigo | Iniciante | Avançado]
  **Última calibração:** [data de hoje]
  ```
  O `CLAUDE.md` já tem a regra de como calibrar ajuda a partir disso e de como recalibrar a cada 15 dias — não precisa repetir a lógica aqui

### `_memoria/estrategia.md`
Preencher com base nas perguntas 7-11. Estrutura:

```markdown
## Diagnóstico 3G — <data>

**Faturamento atual:** [resposta da 7]
**Meta:** [resposta da 7 — número + prazo]
**Ticket médio:** [resposta da 8]
**Canais de venda hoje:** [resposta da 9 — o que funciona e o que já falhou]
**Gargalo atual:** [resposta da 10]

## Foco

**Pra tirar das costas:** [resposta da 11] — candidata a virar skill via /mapear-rotinas
**Próximas prioridades:** [derivar do gargalo — o que ataca o gargalo direto]
**Próximo passo recomendado:** rodar /estrategista na primeira semana pra transformar esse diagnóstico em estratégia completa (oferta, canais, plano 90 dias)
```

Depois de preencher, ler o diagnóstico de volta pro usuário em 3-4 frases no tom 3G (contraste A → B: onde o negócio está → onde quer chegar → o que tá no caminho). É a primeira amostra do que o sistema faz.

### `identidade/design-guide.md`
Se o usuário forneceu cores/fontes/logo (perguntas 12-13), preencher os campos correspondentes. Se não, deixar como está e avisar:
> "Deixei o `identidade/design-guide.md` em branco. Sempre que você definir uma identidade visual, edita lá — as skills de carrossel, proposta e slide leem esse arquivo antes de criar qualquer visual."

### `CLAUDE.md`
Pegar o template correspondente ao perfil escolhido na Fase 1 (`templates/perfis/claude-md-<perfil>.md`), adaptar com o nome do negócio e estrutura de pastas mencionada nas respostas, e sobrescrever o `CLAUDE.md` da raiz.

---

## Fase 4 — Resumo

Mostrar pro usuário o que foi configurado:

```
✓ Perfil aplicado: [perfil]
✓ Nível de IA: [Leigo | Iniciante | Avançado]
✓ Contexto do negócio: _memoria/empresa.md
✓ Tom de voz: _memoria/preferencias.md
✓ Diagnóstico 3G + foco: _memoria/estrategia.md
✓ Marca: identidade/design-guide.md  [preenchida | em branco — preencher depois]
✓ CLAUDE.md adaptado pro perfil [perfil]
```

---

## Fase 5 — Renomear pasta (se necessário)

Se a pasta atual ainda tem nome genérico (detectado na Pré-checagem), gerar slug do nome da empresa (resposta da pergunta 1):
- minúsculas
- sem acentos
- espaços viram hífen
- caracteres especiais removidos

Ex: "Acme Empresa Ltda" → `acme-empresa-ltda`

Mostrar:

> "Última coisa: a pasta ainda tá com nome genérico ('<nome-atual>').
> Pra ter cara do seu negócio, recomendo renomear pra '<slug>'.
>
> Como fazer:
> 1. Fecha o VS Code
> 2. Renomeia a pasta no Finder (Mac) ou Explorer (Windows) — ou no
>    terminal fora dela: `mv <nome-atual> <slug>`
> 3. Abre o VS Code de novo na pasta renomeada
>
> Se preferir outro nome, me fala que eu ajusto a sugestão."

Se a pasta já tem nome próprio (não genérico), pular essa fase.

---

## Fase 6 — Próximos passos

> "Pronto. O 3G IA System já te conhece.
>
> No começo de cada sessão de trabalho, roda `/abrir` — eu carrego tudo
> que combinamos aqui antes da primeira frase. Quando quiser montar uma
> campanha (`/anuncio-google`), ler os números do tráfego (`/relatorio-ads`)
> ou qualquer outra coisa, é só chamar a skill que cabe.
>
> Teu diagnóstico apontou '<gargalo da pergunta 10>' como o que tá
> segurando o crescimento. O próximo passo é rodar `/estrategista` —
> ele transforma esse diagnóstico numa estratégia completa: oferta,
> canais e plano de 90 dias. Recomendo fazer isso na primeira semana.
>
> E você mencionou que repete '<resposta da pergunta 11>' toda semana.
> Quando quiser tirar isso das costas de vez, roda `/mapear-rotinas`
> que eu transformo em skill própria.
>
> Uma parte do sistema merece destaque: o `/instalar-conteudo`. É o
> coração da parte de conteúdo — uma pesquisa profunda de 40 a 60
> minutos (retomável em qualquer ponto) que mapeia tua identidade e
> teu público e destrava todas as skills de conteúdo do sistema.
> Não precisa ser agora: reserva um horário com calma pra rodar.
>
> E se esquecer o que cada comando faz, roda `/dica` — é o manual
> rápido de tudo que o sistema sabe fazer."

Se o gargalo apontado na pergunta 10 envolver audiência, conteúdo ou redes sociais, trocar a frase "Não precisa ser agora: reserva um horário com calma pra rodar." por:

> "Como teu gargalo é justamente conteúdo e presença digital, esse é
> o passo mais importante da tua primeira semana — reserva um horário
> com calma pra rodar."

Se o usuário quiser publicar o trabalho no GitHub, mencionar `/salvar`.

Se o nível de IA (Fase 0) for **Leigo**, detalhar mais essa mensagem final: explicar o que é um "comando" (`/algumacoisa`, digitado direto no chat), como abrir um chat novo no VS Code, e reforçar que não tem como "quebrar" nada testando. Se for **Avançado**, pode ser mais direto e enxuto, sem explicar o básico.

---

## Regras

- Não inventar dados — se a resposta for vaga, registrar do jeito que veio (ou deixar placeholder claro)
- Não escrever "este arquivo será preenchido pelo /instalar" nos arquivos finais — esse aviso só existe nos placeholders, sai depois do /instalar
- O setup deve durar 10 minutos no máximo. Se o usuário estiver enrolando numa pergunta, registra o que tem e segue
- Números do diagnóstico (faturamento, meta, ticket) são sensíveis — registrar sem julgamento e nunca expor em outro contexto sem o usuário pedir
- Não fazer perguntas extras além das listadas acima sem motivo claro
