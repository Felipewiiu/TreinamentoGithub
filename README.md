# Guia de Referência Git e Desenvolvimento

Bem-vindo ao guia definitivo para navegar pelos comandos do Git e dominar os fluxos de desenvolvimento. Seja você um iniciante ou um desenvolvedor experiente, este README será seu recurso principal para entender e utilizar os comandos do Git de forma eficaz.

## Sumário

- [Link para Documentação de Commits Convencionais](https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/)
- [Introdução](#introdução)
- [Configurando e Executando o Projeto](#configurando-e-executando-o-projeto)
- [Trabalhando com Branches](#trabalhando-com-branches)
- [Entendendo os Indicadores de Status de Arquivos no VSCode](#entendendo-os-indicadores-de-status-de-arquivos-no-vscode)
- [Desfazendo Alterações](#desfazendo-alterações)
- [Alterando Mensagens de Commit](#alterando-mensagens-de-commit)
- [Git Reflog: Sua Máquina do Tempo](#git-reflog-sua-máquina-do-tempo)
- [Lixeira do Git: Recuperando Commits Deletados](#lixeira-do-git-recuperando-commits-deletados)
- [Git Bisect: Encontrando Bugs como um Profissional](#git-bisect-encontrando-bugs-como-um-profissional)
- [Git Rebase: Organizando Seus Commits](#git-rebase-organizando-seus-commits)
- [Git Amend: Adicionando ao Seu Último Commit](#git-amend-adicionando-ao-seu-último-commit)
- [Comandos Básicos do Vim](#comandos-básicos-do-vim)

## Introdução

Este repositório serve como um guia abrangente para os comandos do Git e as melhores práticas no desenvolvimento de software. Desde a configuração do seu projeto até técnicas avançadas como rebasing e bisecting, você encontrará tudo o que precisa para otimizar seu processo de desenvolvimento.

## Configurando e Executando o Projeto

### Para executar o projeto localmente:

Certifique-se de ter o Node.js instalado e execute o seguinte comando:

```bash
node app.js
```

## Trabalhando com Branches

### Comandos Básicos de Branches:

- `git checkout`: Alterna entre branches ou restaura arquivos da árvore de trabalho.
- `git checkout -b <nome-da-branch>`: Cria uma nova branch.
- `git branch -a`: Lista todas as branches (local e remoto).
- `git branch`: Lista as branches locais.
- `git switch <nome-da-branch>`: Alterna entre branches.

### Criando uma Cópia Local de uma Branch Remota:

Para criar uma cópia local de uma branch remota, use o seguinte comando:

```bash
git checkout -b <seu-nome-da-branch-local> origin/<nome-da-branch-remota>
```

### Ligando Branches Locais e Remotas:

Para ligar sua branch local a um repositório remoto, use:

```bash
git remote add origin <link-do-repositório>
```

### Enviando Alterações para uma Branch Específica:

Para enviar alterações para uma branch específica, use:

```bash
git push -u origin <nome-da-branch>
```

## Entendendo os Indicadores de Status de Arquivos no VSCode

Já se perguntou o que significam as letras 'M' e 'U' no VSCode? Aqui está um guia rápido:

- **M**: Representa o status 'Modificado', indicando que o arquivo foi modificado mas ainda não foi preparado para o commit.
- **U**: Indica o status 'Não Rastreado', significando que o arquivo é novo e ainda não foi adicionado ao repositório Git.

## Desfazendo Alterações

### Revertendo um Commit:

Para desfazer alterações introduzidas por um commit, use:

```bash
git revert <id-do-commit>
```

Este comando cria um novo commit que desfaz as alterações.

### Excluindo um Commit:

Para remover um commit do histórico, use:

```bash
git reset --hard <id-do-commit>
```

**Observação:** Tenha cuidado ao usar este comando, pois ele exclui permanentemente o commit e suas alterações.

## Alterando Mensagens de Commit

Para alterar a mensagem de um commit ou adicionar novos arquivos a ele, use:

```bash
git commit --amend -m "<nova-mensagem>"
```

## Git Reflog: Sua Máquina do Tempo

O comando `git reflog` mantém um registro de alterações de referência, incluindo movimentos de branches e commits. É útil para recuperar commits ou branches perdidos:

```bash
git reflog
```

## Lixeira do Git: Recuperando Commits Deletados

Se você excluir acidentalmente um commit local e remoto, poderá recuperá-lo da lixeira do Git:

```bash
git show <hash-do-commit>
git cherry-pick <hash-do-commit>
```

## Git Bisect: Encontrando Bugs como um Profissional

O Git bisect é uma ferramenta poderosa para identificar o commit que introduziu um bug:

1. Inicie o processo de bisect:
   ```bash
   git bisect start
   ```
2. Marque o commit ruim:
   ```bash
   git bisect bad
   ```
3. Marque o commit bom:
   ```bash
   git bisect good <commit-bom>
   ```
4. Continue bisectando até encontrar o culpado:
   ```bash
   git bisect visualize
   ```
5. Termine o processo de bisect:
   ```bash
   git bisect reset
   ```

## Git Rebase: Organizando Seus Commits

O Git rebase permite mover ou combinar commits de uma branch para outra:

```bash
git rebase -i <nome-da-branch>
```

## Git Amend: Adicionando ao Seu Último Commit

O comando `git commit --amend` permite adicionar mudanças ao commit anterior:

```bash
git commit --amend
```

## Comandos Básicos do Vim

Aqui estão alguns comandos essenciais do Vim para usuários Linux:

- **Modo de Inserção:**
  - `i`: Inserir texto antes do cursor.
  - `a`: Inserir texto após o cursor.
  - `o`: Inserir uma nova linha abaixo da linha atual.
  - `O`: Inserir uma nova linha acima da linha atual.

- **Modo Normal:**
  - `h`, `j`, `k`,

 `l`: Mover o cursor (esquerda, baixo, cima, direita).
  - `x`: Excluir o caractere sob o cursor.
  - `dd`: Excluir a linha atual.
  - `yy`: Copiar a linha atual.
  - `p`: Colar o texto copiado ou excluído após o cursor.
  - `u`: Desfazer a última operação.
  - `Ctrl + r`: Refazer a última operação desfeita.

- **Navegação:**
  - `G`: Ir para a última linha do arquivo.
  - `gg`: Ir para a primeira linha do arquivo.
  - `:n`: Ir para a linha n (substitua "n" pelo número da linha desejada).
  - `Ctrl + u`: Rolar para cima meia página.
  - `Ctrl + d`: Rolar para baixo meia página.

- **Salvar e Sair:**
  - `:w`: Salvar o arquivo.
  - `:q`: Sair do Vim.
  - `:q!`: Sair do Vim sem salvar as alterações.
  - `:wq` ou `:x`: Salvar e sair do Vim.

Esses comandos ajudarão você a navegar e editar arquivos de forma eficiente usando o Vim.

Agora, munido desse conhecimento, você está pronto para enfrentar qualquer desafio do Git que surgir em seu caminho! Boa codificação! 🚀🔥