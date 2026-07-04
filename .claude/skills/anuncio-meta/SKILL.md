---
name: anuncio-meta
description: >
  Monta TUDO que você precisa pra subir campanha no Gerenciador de Anúncios da Meta
  (Facebook/Instagram): estratégia, estrutura de campanha → conjuntos → anúncios,
  públicos, orçamento distribuído, 2-3 variações de copy por anúncio e checklist
  passo a passo de subida — tudo pronto pra copiar e colar. Checa se o orçamento
  banca o objetivo ANTES de criar. Lê o público do diagnóstico em _memoria/.
  Use quando o usuário pedir "anuncio no instagram", "anúncio no facebook",
  "campanha na meta", "meta ads", "impulsionar", "anunciar no insta",
  ou /anuncio-meta.
---

# /anuncio-meta — Campanha completa pra Meta Ads

Pega o seu produto, o seu bolso e o seu público → entrega um pacote pronto pra copiar no Gerenciador de Anúncios. Da estratégia ao texto de cada anúncio, com o passo a passo de onde clicar.

Fala de dono pra dono. Você não precisa entender de tráfego — precisa responder as perguntas e apertar os botões que o checklist mostrar.

**1 skill = 1 resultado:** um arquivo em `marketing/campanhas/meta/<AAAA-MM-DD>-<produto>.md` com tudo dentro.

## Dependências

- **Contexto do negócio:** `_memoria/empresa.md` (produto, público, região, diferenciais)
- **Diagnóstico e foco:** `_memoria/estrategia.md` (público-alvo do `/instalar`, orçamento, gargalo, histórico)
- **Tom de voz:** `_memoria/preferencias.md`
- **Estratégia (se existir):** `estrategia/<mais-recente>.md` — big idea, oferta, ângulos de anúncio
- **Visual:** `identidade/design-guide.md` — referência pras descrições de criativo
- **Output:** `marketing/campanhas/meta/<AAAA-MM-DD>-<produto>.md` (criar as pastas se não existirem)

> Regra dura: **orçamento que não banca o objetivo = campanha que não sai daqui.** Antes de escrever qualquer anúncio, as contas têm que fechar. Se não fecham, a skill propõe uma estrutura que cabe no bolso — não finge que vai dar certo.

---

## Workflow (6 passos)

### Passo 1 — LER O CONTEXTO primeiro

Antes de qualquer pergunta:

1. Ler `_memoria/empresa.md`, `_memoria/preferencias.md` e `_memoria/estrategia.md`. O `/instalar` já registrou público, números e canais — não perguntar de novo o que já está lá.
2. Se existe estratégia em `estrategia/`, ler a mais recente — oferta, big idea e ângulos de anúncio viram insumo direto dos criativos.
3. Procurar histórico de Meta Ads em `_memoria/` e `marketing/campanhas/meta/` — campanhas anteriores, o que funcionou, o que falhou.

Não listar o que leu. Usar direto na entrevista.

### Passo 2 — ENTREVISTA (uma pergunta por vez)

Regra de ouro: **uma pergunta por vez.** Espera a resposta, usa ela pra calibrar a próxima. Pular o que a memória já responde — só confirmar se o dado parecer velho.

Ordem sugerida:

1. **O que você vai anunciar e por quanto?** Produto/serviço específico + ticket (quanto o cliente paga).
2. **Pra onde o anúncio leva quem clicar?** WhatsApp, site/landing page, formulário da Meta, perfil do Instagram. E a checagem que ninguém faz:
   - WhatsApp → **tem alguém pra responder rápido?** Lead que espera 3 horas esfria. Quem responde e em quanto tempo?
   - Site/landing → **a página existe e vende?** Se não tem landing, formulário da Meta ou WhatsApp são caminhos melhores do que mandar pra home genérica. Falar isso na cara.
   - Formulário → quem recebe os leads e liga/chama em quanto tempo?
3. **Quanto você tem por mês pra investir em anúncio?** Pergunta central — TODA a estrutura sai desse número. Sem constrangimento: R$ 300 e R$ 10.000 geram campanhas diferentes, mas os dois geram campanha.
4. **Público:** ler o público registrado em `_memoria/empresa.md` / `_memoria/estrategia.md` e **mostrar de volta**:
   > "No teu diagnóstico o público registrado é: <público da memória>. Quer anunciar pra esse público ou focar em outro?"
   - Se for outro → entrevistar sobre ele: quem é, idade aproximada, onde mora (cidade/raio), o que essa pessoa curte/segue, qual dor esse produto resolve pra ela.
5. **O que você quer que aconteça de verdade?** Não pergunta técnica — pergunta de negócio: quer gente chamando no WhatsApp? Preenchendo formulário? Comprando direto no site? Conhecendo a marca? A resposta define o objetivo de campanha na Meta.
6. **Já rodou anúncio na Meta antes?** Se sim: o que funcionou, o que queimou dinheiro, tem pixel instalado, tem público que já engajou (seguidores, visitantes do site, lista de clientes)? Se houver histórico em `_memoria/` ou `marketing/campanhas/meta/`, confirmar em vez de perguntar do zero.

Fechar a entrevista quando der pra montar sem chutar. Na dúvida, pergunta mais uma.

### Passo 3 — CHECAGEM DE VIABILIDADE do orçamento (antes de criar qualquer coisa)

Fazer a conta na frente do usuário, com números realistas de Brasil:

**Referências (faixas, variam por nicho — nunca prometer como certeza):**
- CPM (custo por mil visualizações): R$ 15–40
- CPC (custo por clique): R$ 0,80–3,00
- Custo por conversa iniciada no WhatsApp: R$ 3–15
- Custo por lead (formulário): R$ 5–30 (serviço local) / R$ 15–60 (ticket alto/B2B)
- **Mínimo prático por conjunto de anúncios: R$ 15–20/dia.** Abaixo disso o algoritmo não aprende — é dinheiro pingando sem dado.

**A conta que decide a estrutura:**

```
Orçamento mensal ÷ 30 = verba/dia
Verba/dia ÷ R$ 20 = quantos conjuntos o bolso banca (arredondar pra baixo)
Verba mensal ÷ custo estimado por lead/conversa = leads esperados/mês
Leads × taxa de conversão realista (5–20% pra venda assistida) = vendas esperadas
Vendas × ticket = retorno esperado → comparar com o investimento
```

**Se as contas fecham:** mostrar a matemática em 4-5 linhas e seguir.

**Se NÃO fecham** (ex: R$ 300/mês pra vender ticket de R$ 5k direto no frio), dizer na cara:

> "Com R$ 300/mês esse objetivo não para em pé: dá R$ 10/dia, abaixo do mínimo pra 1 conjunto aprender, e venda de R$ 5k no público frio precisa de mais toque do que um clique. Em vez de queimar teu dinheiro, aqui vai o que CABE nesse orçamento: ..."

E propor a estrutura viável — sempre existe uma:
- **Menos conjuntos:** 1 conjunto bem feito > 3 morrendo de fome.
- **Objetivo mais raso do funil:** conversa no WhatsApp em vez de compra; engajamento/vídeo pra aquecer público antes de vender.
- **Remarketing primeiro:** quem já te segue, já visitou, já chamou — público pequeno, barato e quente.
- **Concentrar em menos dias:** R$ 20/dia por 15 dias > R$ 10/dia por 30.

O empresário sai daqui com algo que ele consegue **rodar de fato** — nunca com uma campanha de mentirinha.

### Passo 4 — ESTRATÉGIA + ESTRUTURA (checkpoint antes dos criativos)

Montar e **mostrar pro usuário antes de escrever qualquer anúncio**:

**a) Objetivo de campanha na Meta (traduzido):**

| O que o usuário quer | Objetivo no Gerenciador | Por quê |
|---|---|---|
| Gente chamando no WhatsApp | Engajamento → Mensagem (ou Vendas → WhatsApp, se tiver pixel/histórico) | A Meta otimiza pra quem inicia conversa |
| Leads de formulário | Cadastros (formulário instantâneo) | Lead sem precisar de landing page |
| Venda no site | Vendas (com pixel instalado) | Só vale com pixel + landing que converte |
| Visitas na landing | Tráfego | Barato, mas só clique — usar quando a página vende sozinha |
| Aquecer público | Reconhecimento / Engajamento | Prepara o remarketing, não gera venda direta |

Escolher UM objetivo principal e explicar o porquê em 2-3 frases sem jargão.

**b) Estrutura da campanha** — respeitando o teto de conjuntos do Passo 3:

```
Campanha: [objetivo]-[produto]-[AAAA-MM]
├── Conjunto 1: [objetivo]-[publico]-[data]     ← ex: msg-frio-interesses-2026-07
│   └── Anúncio 1A, 1B, 1C (variações de copy/criativo)
├── Conjunto 2: [objetivo]-[publico]-[data]     ← ex: msg-remarketing-2026-07
│   └── Anúncio 2A, 2B
```

Por conjunto, definir:
- **Público:** localização (cidade + raio), idade, gênero (se fizer sentido), interesses OU Advantage+ (deixar a Meta achar — recomendado pra quem está começando e pra orçamento apertado). Remarketing: seguidores/engajou 90-180 dias, visitantes do site, lista de clientes.
- **Posicionamentos:** Advantage+ (automático) como padrão. Só restringir se houver motivo real.
- **Orçamento diário:** distribuído — remarketing come menos (público menor), frio come mais.

**CHECKPOINT:** mostrar objetivo + estrutura + públicos + distribuição de verba e perguntar:

> "Essa é a estrutura que o teu orçamento banca. Aprova, ou quer ajustar algo antes de eu escrever os anúncios?"

Só avançar com o OK.

### Passo 5 — CRIATIVOS (copy no tom 3G)

Pra cada anúncio, 2-3 variações. Calibrar framework pelo nível de consciência do público (do diagnóstico ou da estratégia, se existir):

- **Consciente do problema** → **PAS:** nomeia a dor → mexe na ferida (o que custa continuar assim) → apresenta a saída.
- **Consciente da solução/produto** → **AIDA:** gancho que para o dedo → interesse (mecanismo/diferencial) → desejo (prova, resultado) → ação clara.
- **Remarketing** → direto ao ponto: oferta + quebra da objeção principal + CTA. Sem re-apresentar a empresa.

Cada variação entrega:

- **Título** (máx 40 caracteres) — benefício ou gancho, nunca o nome da empresa sozinho.
- **Texto primário** — **o gancho DECIDE nas 3 primeiras linhas** (é o que aparece antes do "...ver mais"). Frases curtas. Contraste A → B (onde o cliente está → onde ele chega). Zero jargão de guru.
- **Descrição** (opcional, curta) — reforço ou quebra de objeção.
- **CTA do botão** — o que existe no Gerenciador: "Enviar mensagem", "Saiba mais", "Cadastre-se", "Comprar agora". Casar com o destino.
- **Criativo sugerido** — descrição pro designer (ou pro dono fazer no celular): o que aparece na imagem/vídeo, que texto vai na arte (pouco — a Meta pune texto demais), formato (1:1 feed, 9:16 stories/reels). Consultar `identidade/design-guide.md` pra cores e estilo.

Seguir `_memoria/preferencias.md` estritamente. Se o público não fala "escalar", o anúncio também não fala.

### Passo 6 — SALVAR o pacote + checklist de subida

Salvar em `marketing/campanhas/meta/<AAAA-MM-DD>-<produto-kebab-case>.md`:

```markdown
---
produto: "<produto>"
data: AAAA-MM-DD
objetivo_meta: "<objetivo de campanha>"
destino: "<WhatsApp | landing | formulário | perfil>"
orcamento_mensal: "R$ 0.000"
orcamento_diario: "R$ 00"
publico_base: "<do diagnóstico | novo>"
---

# Campanha Meta — <Produto>

## Estratégia em 5 linhas
<objetivo, por quê esse objetivo, quanto vai investir, o que esperar em números
(faixa, nunca promessa), quando reavaliar>

## A conta
<matemática do Passo 3: verba/dia, conjuntos, leads esperados, retorno esperado>

## Estrutura

### Campanha: <nome no padrão>
- Objetivo: <objetivo no Gerenciador>
- Orçamento: <no nível da campanha ou do conjunto — dizer qual>

### Conjunto 1: <nome no padrão [objetivo]-[publico]-[data]>
- **Público:** <localização + raio, idade, interesses ou Advantage+>
- **Posicionamentos:** <Advantage+ | detalhar>
- **Orçamento diário:** R$ <XX>

#### Anúncio 1A
- **Título:** <máx 40 chars>
- **Texto primário:** <gancho nas 3 primeiras linhas>
- **Descrição:** <curta>
- **Botão (CTA):** <opção real do Gerenciador>
- **Criativo:** <descrição pro designer + formato>

#### Anúncio 1B ... (2-3 variações por anúncio)

### Conjunto 2 ... (repetir o bloco)

## Passo a passo pra subir (você não precisa saber de tráfego)

1. Acessa **business.facebook.com** → Gerenciador de Anúncios (conta certa no topo)
2. Botão verde **+ Criar** → escolhe o objetivo **<objetivo>** → Continuar
3. Nomeia a campanha: cola `<nome da campanha>`
4. No conjunto: cola o nome `<nome do conjunto>`, define orçamento diário R$ <XX>
5. Em **Público:** <instrução exata — localização, raio, idade, interesses ou deixar Advantage+>
6. Em **Posicionamentos:** deixa "Advantage+" (automático)
7. No anúncio: cola o nome, sobe a imagem/vídeo, cola o **Texto primário** no campo
   "Texto principal", o **Título** em "Título", a **Descrição** em "Descrição",
   escolhe o botão **<CTA>** e confere o destino (<link/WhatsApp/formulário>)
8. Repete pros outros anúncios do conjunto (botão "Duplicar" economiza tempo)
9. **Publicar** — a Meta revisa em até 24h
10. Antes de publicar: confere forma de pagamento em Configurações → Pagamentos

## Primeiros 7 dias — o que olhar (e o que ignorar)

- **Dias 1-3: NÃO MEXE.** O algoritmo está aprendendo. Mexeu, zerou o aprendizado.
- Olhar 1x por dia, só isto:
  - **Custo por resultado** (conversa/lead) — está dentro da faixa da conta lá de cima?
  - **CTR** (% de quem viu e clicou) — abaixo de 1% = criativo fraco, anota pra trocar depois do dia 7
  - **Leads chegando estão sendo respondidos?** — o furo geralmente é aqui, não no anúncio
- **Dia 7, decide:**
  - Custo por resultado dentro da faixa → mantém mais 7 dias
  - Um anúncio claramente melhor → pausa os piores, deixa a verba no vencedor
  - Custo 2x acima da faixa e sem melhora → pausa o conjunto, volta aqui pra ajustar
- **Escalar:** só depois de 14 dias bons, subindo verba no máximo 20% por vez

Pra ler os números comigo: roda `/relatorio-ads` a partir do dia 7.
```

No fim, mostrar no chat um resumo (estrutura + verba + onde salvou) e fechar:

> "Pacote completo em `marketing/campanhas/meta/<arquivo>`. Sobe seguindo o passo a passo e no dia 7 roda `/relatorio-ads` que a gente lê os números juntos."

Se surgiu informação nova relevante (orçamento de mídia definido, público novo validado, primeiro tráfego pago do negócio), perguntar se atualiza `_memoria/estrategia.md`.

---

## Regras

- **Contexto primeiro.** Ler `_memoria/` e `estrategia/` antes de perguntar. Não perguntar o que já está escrito.
- **Uma pergunta por vez** na entrevista. Nunca despejar questionário.
- **Viabilidade antes de criação.** A conta do Passo 3 é obrigatória. Orçamento que não banca o objetivo → dizer na cara e propor a estrutura que cabe. Nunca entregar campanha que não para em pé.
- **Mínimo R$ 15-20/dia por conjunto.** Menos conjuntos bem alimentados > estrutura bonita passando fome.
- **Checkpoint antes dos criativos.** Estratégia + estrutura aprovadas primeiro. Sem OK, sem copy.
- **Destino tem que aguentar.** WhatsApp sem quem responda, landing que não existe, formulário que ninguém olha — apontar o furo antes de mandar tráfego pra ele.
- **Nunca prometer resultado.** CPM, CPC e custo por lead são faixas de referência — sempre apresentar como estimativa a validar nos primeiros 7 dias.
- **Nomes no padrão** `[objetivo]-[publico]-[data]` em tudo — campanha, conjunto e anúncio. Sem isso o relatório vira adivinhação.
- **Advantage+ como padrão** pra posicionamento e, com orçamento apertado ou sem histórico, pra público também. Segmentação manual só com motivo real.
- **Copy no tom 3G:** gancho nas 3 primeiras linhas, frases curtas, contraste A → B, zero jargão de guru. Seguir `_memoria/preferencias.md` estritamente.
- **Checklist pra leigo.** O passo a passo diz onde clicar e o que colar em cada campo. Quem nunca abriu o Gerenciador consegue subir sozinho.
- **Um arquivo, um resultado.** Tudo em `marketing/campanhas/meta/<AAAA-MM-DD>-<produto>.md`.
