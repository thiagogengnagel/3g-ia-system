---
name: dica
description: >
  Manual rápido do 3G IA System. Mostra o mapa de todas as skills instaladas — o que cada
  comando faz e quando usar — organizado por área (núcleo, estratégia, tráfego pago,
  conteúdo), e sugere o próximo passo conforme o estágio do setup. Use quando pedirem
  "/dica", "que comandos tem", "quais skills existem", "esqueci os comandos",
  "o que cada skill faz", "manual do sistema", "como uso o sistema", "me lembra os comandos".
---

# /dica — Manual rápido das skills

Esse comando é o mapa do sistema. Quem usa esquece o que cada `/comando` faz — o `/dica`
resolve isso em uma tela, sem a pessoa precisar abrir arquivo nenhum.

## Como montar o manual

**Nunca usar uma lista decorada.** Sempre ler as skills reais instaladas, porque o sistema
cresce (skills novas entram via `/mapear-rotinas`, `/atualizar` ou criação manual) e o
manual não pode ficar desatualizado.

1. Listar as pastas de `.claude/skills/` (cada pasta é uma skill).
2. Ler o frontmatter (`name` e `description`) do `SKILL.md` de cada uma.
3. Resumir cada skill em UMA linha: o que faz + quando usar, em linguagem de dono de
   negócio — sem termo técnico, sem copiar a description inteira.

## Formato da resposta

Apresentar o manual agrupado por área, nesta ordem:

```
MANUAL RÁPIDO — 3G IA SYSTEM

DIA A DIA (núcleo)
/abrir            — roda no começo de toda sessão: carrega teu contexto antes da primeira frase
/instalar         — setup inicial do sistema (só na primeira vez ou pra refazer)
/salvar           — salva teu trabalho no GitHub (backup)
/atualizar        — varredura na memória do sistema pra ver se algo ficou desatualizado
/novo-projeto     — abre a estrutura de um projeto novo
/mapear-rotinas   — transforma uma tarefa que você repete toda semana em skill própria
/dica             — este manual

ESTRATÉGIA
/estrategista     — estratégia completa de marketing: oferta, canais e plano de 90 dias

TRÁFEGO PAGO
/anuncio-meta     — monta campanha pronta pra subir no Gerenciador da Meta (Instagram/Facebook)
/anuncio-google   — mesma coisa, pro Google Ads
/relatorio-ads    — lê os números das tuas campanhas e traduz em decisão
/otimizar-ads     — diagnóstico de campanha a partir de print: o que pausar, manter e escalar

CONTEÚDO — MÉTODO EU
/instalar-conteudo           — o coração do conteúdo: pesquisa profunda de identidade e público (40-60 min, retomável) que destrava as skills abaixo
/metodo-eu-2-analise-produto — diagnóstico dos teus produtos, esteira e preços
/estrategia-conteudo         — estratégia mãe de conteúdo do período (pilares HERO/HELP/HUB)
/metodo-eu-4a-instagram      — transforma a estratégia em posts prontos de Instagram
/metodo-eu-4b-tiktok         — transforma a estratégia em roteiros prontos de TikTok
/metodo-eu-5-redatora        — refina qualquer texto na voz da tua marca, ou cria avulso
/metodo-eu-6-metricas        — lê os números do conteúdo e diz o que ajustar
```

As linhas acima são referência de tom e tamanho — o conteúdo real vem da leitura dos
frontmatters. Skill instalada que não estiver nas áreas acima (ex: skill criada pelo
`/mapear-rotinas`) entra num grupo final chamado **SKILLS DO SEU NEGÓCIO**.

## Próximo passo sugerido

Depois do manual, sugerir UM próximo passo conforme o estágio (verificar os arquivos):

- `_memoria/empresa.md` vazio ou placeholder → "Você ainda não rodou o setup. Começa pelo `/instalar`."
- `_memoria/estrategia.md` sem estratégia gerada e sem pasta `estrategia/` → "Teu diagnóstico tá feito, mas ainda não virou plano. Roda `/estrategista`."
- `conteudo/metodo-eu/1-mapeamento.md` não existe → "A parte de conteúdo ainda tá trancada. Quando tiver um tempo reservado, roda `/instalar-conteudo` — é ele que destrava tudo."
- `conteudo/metodo-eu/1-mapeamento.md` existe mas não há `3-estrategia-*.md` → "Teu mapeamento tá pronto. O próximo passo é `/metodo-eu-2-analise-produto` e depois `/estrategia-conteudo`."
- Tudo em dia → "Sistema completo em uso. No dia a dia: `/abrir` no começo da sessão e a skill que a tarefa pedir."

## Regras

- Nunca inventar skill que não existe na pasta — o manual reflete o que está instalado
- Uma linha por skill; se a description for longa, resumir, não colar
- Sem jargão técnico e sem sigla sem tradução; linguagem de dono de negócio
- Sem emoji
- Sugerir apenas UM próximo passo, o mais relevante pro estágio — não uma lista de tarefas
- Esse comando não escreve nem altera arquivo nenhum — só mostra o manual
