# ![IST Logo](./IST_Logo.png) Resumos MEEC

## Introdução

Bem vindos ao site comunitário de resumos de MEEC.  
Criado por um grupo de alunos gostosos e baseado
no site de LEIC-A.

## Links Uteis

## Contribuidores 💛

## Como Contribuir

#### Instalar Ferramentas

Para correr o código localmente, é necessário instalar as seguintes ferramentas: `git` e `nodejs`.

##### Para verificar se já tens tudo instalado coiso

##### Se ainda precisares de instalar

#### Windows

1. Fazer [download do `git`](http://git-scm.com/) e instalar o executável.
2. Fazer [download do `node`](https://nodejs.org/en/) e instalar a última versão LTS (à data, 14.X LTS).

#### Linux

1. Instalar o `git` e o `node` pelo package manager da distribuição. Atenção que o `node` em Debian/Ubuntu/etc está desatualizado.
   Recomendo seguir [este tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04#option-3-%E2%80%94-installing-node-using-the-node-version-manager) para ter o Node 14 LTS.

### Contribuir

1. Fazer fork do repositório no GitHub, clickar no botão "Fork" no canto superior direito;

2. Fazer clone da vossa fork:

```bash
git clone https://github.com/<vosso username do github>/resumos-meec.git
```

3. Dar setup do remote upstream

```bash
git remote add remote upstream https://github.com/SparklingRita/resumos-meec.git
```

4. Instalar dependências

```bash
cd resumos-meec
npm i
```

### Alterar conteúdos

::: warning
Antes de alterar qualquer conteúdo, deves criar um novo `branch` apenas para essa alteração.
Não deves repetir nomes de branches.

Para o fazer no VSCode, faz `Ctrl+Shift+P` , seleciona **Git: Create Branch From** , depois dá um nome (ex: `acomp-aula1`) e seleciona `main`.

Para fazer o mesmo, mas pelo terminal, é necessário o comando:

```bash
git checkout -b nome-do-branch
```

:::

Para contribuires com os teus próprios resumos, precisas de editar os ficheiros `.md` (ficheiros markdown) que estão na pasta `src`.  
Para alterar os links na sidebar, é necessário alterar o ficheiro `src/.vuepress/config.js` para o respetivo tema/título da matéria.  
Se nunca trabalhaste com esta linguagem, tens [aqui](https://www.markdownguide.org/basic-syntax) um guia para te ajudar, é bastante simples.

Para iniciar o servidor local, para ver como ficou, correr o comando:

```bash
npm run dev
```

### Últimos passos

Já está praticamente tudo feito, basta fazer `commit` e `push` pela interface do VSCode, ou então, pelo terminal:

```bash
git add .
git commit -m "mensagem"
git push
```

::: tip
Se forem ao site e ainda não estiver lá, não se preocupem, demora algum tempo.
Só serão aceites resumos que realmente acrescentem algo, para que não haja repetição de conteúdos.
Agradecemos todas as contribuições :)
:::

### Para as próximas vezes

Caso seja a primeira vez que estão a contribuir, este passo não é necessário, só precisarão para as próximas contribuições.
Antes de voltar a fazer alterações, tem de ser necessário atualizar a `fork`, para isso, têm de voltar para o `branch main`, fazer `pull` do upstream e `push` para o origin:

```bash
git checkout main
git pull upstream main
git push
```

A partir daqui, é criar um novo branch e fazer as alterações, tal como da última vez.
