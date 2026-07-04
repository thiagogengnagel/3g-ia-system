---
name: otimizar-ads
description: >
  Diagnóstico sob demanda de campanha de tráfego pago (Meta Ads ou Google Ads) a partir
  de print do Gerenciador, métricas coladas no chat ou CSV. Acha ONDE o funil vaza
  (entrega → criativo → público → destino/atendimento → oferta), dá semáforo por métrica
  e devolve plano de ação priorizado com o passo a passo de onde clicar — em linguagem
  de dono, pra decidir AGORA o que pausar, o que manter e o que escalar.
  Use quando o usuário pedir "analisa minha campanha", "olha esse print", "campanha tá
  cara", "otimizar anúncio", "o que pausar", "meu anúncio não tá dando resultado",
  ou /otimizar-ads.
---

# /otimizar-ads — Diagnóstico e otimização de campanha na hora

Você tira print do Gerenciador, arrasta pro chat → sai com o veredicto: o que tá bom, o que tá vazando e o que fazer agora. Sem esperar relatório semanal, sem precisar entender de tráfego.

Fala de dono pra dono. Toda sigla traduzida na primeira vez. Toda ação com o caminho de onde clicar.

**Diferença pro `/relatorio-ads`:** relatório é a leitura semanal completa a partir dos exports. Isso aqui é o pronto-socorro — print na mesa, diagnóstico, decisão. Se a necessidade for acompanhamento recorrente, a skill encaminha pro `/relatorio-ads`.

**1 skill = 1 resultado:** diagnóstico no chat + arquivo em `marketing/campanhas/otimizacoes/<AAAA-MM-DD>-<campanha>.md`.

## Dependências

- **Contexto:** `_memoria/empresa.md` (produto, ticket), `_memoria/estrategia.md` (foco, público, orçamento)
- **Tom de voz:** `_memoria/preferencias.md`
- **Planejado vs realizado:** `marketing/campanhas/meta/` e `marketing/campanhas/google/` — se a campanha nasceu do `/anuncio-meta` ou `/anuncio-google`, comparar o previsto com o que aconteceu
- **Inputs aceitos:** print/screenshot do Gerenciador, métricas coladas como texto, CSV em `dados/`
- **Output:** `marketing/campanhas/otimizacoes/<AAAA-MM-DD>-<campanha-kebab-case>.md` (criar a pasta se não existir)

> Regra dura: **1-2 mudanças por vez.** Quem mexe em tudo de uma vez nunca descobre o que funcionou. O plano prioriza — não despeja.

---

## Workflow (5 passos)

### Passo 1 — EXTRAIR os dados do que chegou

**Se veio print/screenshot:** ler a imagem e extrair TODAS as métricas visíveis — nome da campanha, conjuntos, anúncios, status (ativo/pausado/em análise), verba (diária ou total), valor gasto, resultados, custo por resultado, CTR, CPM, CPC, frequência, alcance, impressões, cliques, período selecionado. Transcrever numa tabela e **mostrar pro usuário confirmar** antes de diagnosticar — print borrado gera diagnóstico errado.

**Se veio texto colado:** organizar os números na mesma tabela.

**Se veio CSV:** ler de `dados/` e extrair as mesmas colunas.

**Detectar a plataforma** pela cara dos dados:
- Meta: "conjunto de anúncios", "resultados", "custo por resultado", "frequência", "alcance", CBO/Advantage+
- Google: "grupo de anúncios", "palavras-chave", "índice de qualidade", "parcela de impressão", "conversões", CPA
- Ambíguo → perguntar: "Esse print é do Gerenciador da Meta ou do Google Ads?"

**Ler o contexto:** `_memoria/estrategia.md` (ticket, público, orçamento planejado) e `marketing/campanhas/` — se a campanha veio do `/anuncio-meta` ou `/anuncio-google` (nome no padrão `[objetivo]-[publico]-[data]` entrega isso de bandeja), abrir o arquivo e comparar previsto vs realizado.

### Passo 2 — PERGUNTAR só o que faltar (uma pergunta por vez)

Dados essenciais pro diagnóstico. Se o print ou a memória já responde, **não perguntar**:

1. **Período** — esses números são de quantos dias? (Campanha com 2 dias não se julga igual a campanha com 30.)
2. **Objetivo da campanha** — o que "resultado" significa aqui: conversa no WhatsApp, lead de formulário, venda no site, clique?
3. **Ticket** — quanto o cliente paga pelo produto anunciado? (Sem isso não dá pra saber se o custo por resultado compensa.)
4. **Destino** — pra onde o anúncio manda quem clica, e o que acontece depois? Se for WhatsApp/formulário, a pergunta que ninguém faz: **"Os leads estão sendo respondidos em quanto tempo?"**

Uma pergunta por vez. Fechar quando der pra diagnosticar sem chutar.

### Passo 3 — DIAGNÓSTICO EM CAMADAS: achar onde o funil vaza

Percorrer as camadas **nesta ordem** — o problema de cima contamina a leitura de baixo:

**Camada 1 — Entrega: o dinheiro tá saindo?**
- Verba gastando de fato? Gasto muito abaixo da verba diária = problema de entrega (público pequeno demais, lance baixo, anúncio reprovado/em análise).
- Conjunto "em aprendizado" ou "aprendizado limitado"? Limitado = poucos resultados por semana pro algoritmo aprender — verba baixa demais ou conjuntos demais (régua: mínimo R$ 15-20/dia por conjunto).
- Frequência acima de 3? O mesmo público tá vendo o anúncio repetido — saturando. Acima de 4 é ruído pago.

**Camada 2 — Criativo: o anúncio para o dedo?**
- CTR (% de quem viu e clicou) abaixo de 1% = anúncio fraco: gancho não segura, imagem não para o scroll.
- CTR ok (≥1%) mas custo por resultado alto = o anúncio faz o trabalho dele; o problema tá mais fundo. Continuar descendo.

**Camada 3 — Público: o anúncio tá chegando na pessoa certa?**
- CPM (custo por mil visualizações) fora da faixa R$ 15-40 = público caro ou disputado demais (ou estreito demais).
- Frequência alta com público pequeno = esgotou quem tinha pra ver.
- Vários conjuntos com público parecido = sobreposição — os conjuntos disputam leilão entre si.

**Camada 4 — Destino/atendimento: o clique vira conversa? A conversa vira venda?**
- Clique barato, CTR bom, mas resultado não aparece = o vazamento é DEPOIS do anúncio: landing que não convence, WhatsApp que demora horas pra responder, formulário que ninguém olha.
- **Esse é o furo mais comum** — e nenhum ajuste de campanha conserta. Se o lead espera 3 horas por resposta, o problema não é o anúncio. Dizer na cara.

**Camada 5 — Oferta/economia: a conta fecha?**
- Custo por resultado × taxa de conversão real = CAC (custo de aquisição de cliente). Comparar com ticket e margem.
- Ex.: lead a R$ 20, converte 10% → cliente custa R$ 200. Ticket R$ 150 = prejuízo em cada venda. Nenhuma otimização de campanha salva isso — o problema é a oferta. Apontar `/estrategista`.

**Réguas de referência (Brasil, faixas — nunca certeza):** CPM R$ 15-40 · CPC R$ 0,80-3,00 · conversa WhatsApp R$ 3-15 · lead formulário R$ 5-30 (local) / R$ 15-60 (ticket alto/B2B) · CTR saudável ≥ 1% · frequência boa 1,5-3,0 · mínimo R$ 15-20/dia por conjunto. Variam por nicho — usar como faixa, apresentar como estimativa.

**Google Ads:** mesma lógica em camadas, réguas próprias — CTR de Search saudável ≥ 3-5% (rede de pesquisa é gente buscando, não scroll), conv. rate < 1% em Search = destino ou palavra-chave errada, olhar termos de pesquisa que gastam sem converter (virar negativas) e parcela de impressão perdida por orçamento/classificação.

### Passo 4 — MONTAR a entrega

Estrutura obrigatória (no chat e no arquivo):

**a) Veredicto em 3 linhas** — tom 3G, contraste A → B: o que tá bom, o que tá vazando, a decisão. Quem lê só isso já sabe o que fazer.

**b) Semáforo por métrica** — tabela com cada métrica disponível:

| Métrica | Valor | Faixa esperada | Status | O que significa |
|---|---|---|---|---|
| CTR (% de quem viu e clicou) | 0,6% | ≥ 1% | 🔴 | O anúncio não tá parando o dedo |
| Custo por conversa | R$ 8 | R$ 3-15 | 🟢 | Dentro do esperado |

Traduzir toda sigla na primeira vez. Verde = dentro da faixa; amarelo = no limite ou tendência ruim; vermelho = fora da faixa, pede ação.

**c) Diagnóstico** — em qual camada o funil vaza e por quê, com a evidência dos números ("CTR 1,4% mas custo por lead 3x a faixa → o anúncio entrega, o vazamento é depois do clique"). Se houver campanha planejada em `marketing/campanhas/`, incluir previsto vs realizado.

**d) Plano de ação priorizado** — 3-5 ações em ordem de impacto. Cada ação com o COMO pra leigo:

> **1. Pausa o anúncio 2B** (custo por conversa R$ 27 — 3x o do 2A): Gerenciador → abre a campanha `msg-frio-2026-06` → aba Anúncios do conjunto 2 → desliga a chave azul do 2B. A verba dele passa automático pros que ficam.

Incluir sempre o bloco **"O que NÃO mexer"**:
- Conjunto nos dias 1-3 = em aprendizado. Mexeu, zerou o aprendizado.
- Nunca tudo de uma vez — as 1-2 primeiras ações do plano, só.
- Escalar verba: no máximo +20% por vez, e só depois de 7-14 dias bons.

**e) O que esperar + quando voltar** — prazo pra reavaliar (em geral 3-7 dias após a mudança), QUAL número olhar e qual faixa indica que funcionou. Nunca prometer resultado — sempre "a expectativa é X cair pra faixa Y; se não cair, o próximo suspeito é Z".

### Passo 5 — SALVAR + ganchos

Salvar em `marketing/campanhas/otimizacoes/<AAAA-MM-DD>-<campanha-kebab-case>.md`:

```markdown
---
campanha: "<nome>"
plataforma: meta | google
data: AAAA-MM-DD
periodo_analisado: "<X dias | DD/MM a DD/MM>"
gasto: "R$ 0.000"
custo_por_resultado: "R$ 00"
vazamento_principal: "entrega | criativo | publico | destino | oferta"
acoes: 0
reavaliar_em: AAAA-MM-DD
---

# Otimização — <campanha>

## Veredicto
<3 linhas>

## Semáforo
<tabela>

## Diagnóstico
<camada + evidência + previsto vs realizado se houver>

## Plano de ação
<3-5 ações com passo a passo + "O que NÃO mexer">

## O que esperar
<prazo + número a olhar>
```

Mostrar tudo no chat (o arquivo é o registro) e fechar com os ganchos que couberem:

- **Otimização virando rotina** (segundo diagnóstico da mesma conta): "Isso tá virando recorrente — quer rodar o `/relatorio-ads` toda semana? A leitura comparativa pega tendência que o print isolado não mostra."
- **Criativo fraco** (CTR vermelho): "O gargalo é o anúncio em si. Quero reescrever a copy agora? Uso o padrão do `/anuncio-meta` — 2-3 variações prontas pra colar."
- **Aprendizado durável** (público que não performa, ângulo que sempre ganha, faixa de custo validada do nicho): perguntar se atualiza `_memoria/estrategia.md` com uma linha — ex: "público frio por interesses não performou em 2 campanhas; remarketing converte a 1/3 do custo".

---

## Regras

- **Confirmar a extração do print antes de diagnosticar.** Mostrar a tabela de métricas lidas e pegar o OK. Print borrado ou número ilegível = "dado incompleto", nunca chute.
- **Nunca inventar números.** Diagnóstico só sobre o que está no print/texto/CSV. O que faltar, perguntar ou marcar como não avaliado.
- **Uma pergunta por vez.** Só o que a imagem e a memória não respondem.
- **Camadas em ordem.** Entrega → criativo → público → destino → oferta. Não pular pra "troca o criativo" sem checar se a verba sequer tá gastando.
- **1-2 mudanças por vez.** Plano priorizado, com "o que NÃO mexer" explícito. Quem mexe em tudo não sabe o que funcionou.
- **Dias 1-3 são sagrados.** Conjunto em aprendizado não se mexe. Escalar = máximo +20% por vez.
- **Destino furado = dizer na cara.** Se o lead não é respondido rápido ou a landing não converte, nenhum ajuste de anúncio resolve — falar isso ANTES de sugerir qualquer mudança na campanha.
- **Se a economia não fecha** (custo por resultado × conversão > ticket/margem), o alerta principal é a OFERTA, não a campanha. Apontar `/estrategista`.
- **Benchmarks são faixas, nunca promessa.** CPM, CPC, custo por lead variam por nicho — sempre "faixa de referência", nunca "vai ficar em X".
- **Toda ação com o caminho de onde clicar.** Quem nunca abriu o Gerenciador executa o plano sozinho.
- **Toda sigla traduzida na primeira vez.** CTR, CPM, CAC — linguagem de dono.
- **Meta E Google.** Detectar pela cara dos dados; ambíguo = perguntar. Réguas certas pra cada plataforma.
- **Tom 3G do começo ao fim.** Direto, frases curtas, contraste A → B, zero jargão de guru. Seguir `_memoria/preferencias.md`.
- **Um arquivo, um resultado.** `marketing/campanhas/otimizacoes/<AAAA-MM-DD>-<campanha>.md`.
