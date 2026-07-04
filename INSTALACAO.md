# Instalação do zero — passo a passo

> Guia pra quem nunca mexeu com nada disso. Segue na ordem que funciona.
> Tempo total: 20-30 minutos. Só precisa fazer uma vez.

---

## O que você vai instalar

1. **Visual Studio Code** — o programa onde tudo acontece
2. **Git** — o que baixa e salva o sistema
3. **Node.js** — o motor que o Claude Code precisa pra rodar
4. **Claude Code** — a IA que vai operar o seu negócio
5. **3G IA System** — o sistema em si

---

## Passo 1 — Visual Studio Code

1. Acesse [code.visualstudio.com](https://code.visualstudio.com)
2. Clique no botão azul de download (ele detecta se você usa Windows ou Mac)
3. Abra o arquivo baixado e siga o instalador (pode deixar tudo no padrão, só "Avançar")

**Windows:** na tela de opções, marque "Adicionar ao PATH" se aparecer.

---

## Passo 2 — Git

**Windows:**
1. Acesse [git-scm.com/download/win](https://git-scm.com/download/win)
2. Baixe e instale (pode clicar "Next" em tudo — o padrão funciona)

**Mac:**
1. Abra o app **Terminal** (busca no Spotlight: `terminal`)
2. Digite `git --version` e aperte Enter
3. Se pedir pra instalar as "Command Line Tools", aceite e aguarde

---

## Passo 3 — Node.js

1. Acesse [nodejs.org](https://nodejs.org)
2. Baixe a versão **LTS** (o botão principal)
3. Instale com tudo no padrão

---

## Passo 4 — Claude Code

Você precisa de uma conta no Claude com plano pago (Pro ou superior).
Se ainda não tem, crie em [claude.ai](https://claude.ai).

1. Abra o VS Code
2. No menu de cima: **Terminal → New Terminal** (abre um painel embaixo)
3. Cole esse comando e aperte Enter:

```
npm install -g @anthropic-ai/claude-code
```

4. Quando terminar, digite:

```
claude
```

5. Na primeira vez, ele abre o navegador pra você fazer login na sua
   conta Claude. Faz o login e volta pro VS Code.

Se apareceu a tela de boas-vindas do Claude no terminal, deu certo.

---

## Passo 5 — Baixar o 3G IA System

Ainda no terminal do VS Code (se o Claude estiver aberto, aperte
`Ctrl+C` duas vezes pra sair), cole uma linha de cada vez:

```
cd Documents
```

```
git clone https://github.com/thiagogengnagel/3g-ia-system.git
```

```
cd 3g-ia-system
```

```
code .
```

Vai abrir uma janela nova do VS Code já dentro do sistema. Pode fechar a antiga.

---

## Passo 6 — Ligar o sistema

Na janela nova: **Terminal → New Terminal**, e digite:

```
claude
```

Quando o Claude abrir, digite:

```
/instalar
```

Ele vai te entrevistar sobre o seu negócio (5-7 minutos). Responde com
calma — quanto melhor as respostas, melhor o sistema te conhece.

---

## Pronto

A partir de agora, o dia a dia é: abrir o VS Code na pasta do seu
negócio, abrir o terminal, digitar `claude` e trabalhar.

- Começando uma sessão? Roda `/abrir`
- Terminando? Roda `/salvar`

Qualquer dúvida no caminho, chama a gente: [@thiagoarthur3g](https://instagram.com/thiagoarthur3g)

---

## Deu erro?

**"git não é reconhecido" / "command not found: git"** — o Git não
instalou ou o VS Code abriu antes da instalação. Feche o VS Code
completamente e abra de novo.

**"npm não é reconhecido"** — mesma coisa com o Node.js. Feche o VS
Code e abra de novo. Se persistir, reinstale o Node.js.

**O login do Claude não abre o navegador** — copie o link que aparece
no terminal e cole no navegador manualmente.
