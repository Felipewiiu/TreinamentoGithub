

## Link para documentações

+ [Convertional commit: ](https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/)

<h1> Sistema de cadastro de jogos</h1>

> Status: em desemvolvimento
Para rodar esse projeto na sua máquina, por favor digite:

```
node app.js
```

# Comandos na branch

> `git checkout` -->  Alternar ramificações ou restaurar arquivos da árvore de trabalho

> `git checkout -b` --> Faz a criação de uma nova branch

> `git branch -a` --> lista todas as branchs tanto local quanto remoto

> `git branch` --> Lista as branchs

> `git switch` --> Faz a troca de branchs

# Para criar uma cópia da branch remota

> Basta Colocar um nome da branch local e apontar a origem com o link do repositório que deseja copiar

`git checkout -b <nome-do-seu-branch-local> origin/<nome-do-branch-remoto>`

# Para fazer o link entre a branch local e remota

`git remote add origin https://github.com/Felipewiiu/ApiContext.git`

# Para definir para qual branch se deve fazer o upload

`git push -u origin master`

## Sinalizações em arquivos do VSCode

Mas o que isso significa as letras M e U do vscode?

![alt text](image.png)

+ M: A letra M representa o estado Modified, do português modificado. Isso significa que o arquivo já existia no repositório, mas que recebeu alguma modificação que ainda não foi registrada no Git.

+ U: A letra U representa o estado Untracked, do português não rastreado. Isso significa que o arquivo ainda não existia no repositório e que ainda não teve seu registro (commit) feito no Git.

## Desfazendo um commit

Para que possamos desfazer alterações em nosso código basta usar o comando: 

````
git revert mais [id] do commit

````
esse comando funciona como um control + z em todas as alterações do arquivo e nos traz um novo commit.

## Apagando um commit

Para que possamos apagar um commit usamos o seguinte código:

````javascript
git reset --hard a3322db2eb6f82162977169f5461fc93b81bfac1

````

**OBS:** _PAra que esse comando funcione precisamos passar o ID do commit anterios._

## Comando para se alterar o nome de um commit

Para que possamos mudar o nome de um commit ou adicionarmos um novo arquivo usamos o seguinte código:

````
git commit --amend -m [novaMensagemColoqueAqui]

````
É importante destacar que os comandos do Git que permitem modificar o histórico de commits devem ser utilizados com prudência e apenas quando o commit em questão ainda não foi enviado ao repositório remoto, ou seja, quando ele existe apenas no seu repositório local.

Modificar um commit que já se tornou público, ou seja, aquele que já foi enviado ao GitHub ou a qualquer outro repositório remoto, pode acarretar problemas consideráveis na colaboração com as outras pessoas e na integridade do histórico de um projeto.

Em situações de colaboração em equipe, é essencial manter a integridade do histórico de commits, pois qualquer modificação em um commit que outras pessoas estejam trabalhando pode resultar em conflitos e dificuldades na colaboração.

É recomendável evitar a modificação excessiva do histórico de commits, uma vez que isso pode tornar o histórico confuso. O histórico deve ser uma representação precisa do progresso do projeto ao longo do tempo.


## Git reflog


O git reflog é uma ferramenta muito útil no Git que mantém um registro de referências de cabeças (heads), o que inclui mudanças nos ponteiros de branches e commits mesmo que não estejam mais visíveis no histórico normal de commits. Ele é útil em situações em que você acidentalmente removeu um branch ou redefiniu o HEAD para um commit anterior e precisa recuperar o estado anterior.

````
Comando: git reflog

````

## Alixeira do git

Imagine o cenário em que você apaga um commit tanto no local, quanto no remoto. A maneira de se recuperar esse commit é indo na "lixeira" do git. Lá fica as informações que um dia existiram na linha do tempo do git e é possível recupera-las com o comando:

````
Comando que mostra o commit: git show [hash_do_commit]

Comando que recupera o commit: git cherry-pick

````

## Gitbisect

O git bisect é uma ferramenta poderosa no Git usada para encontrar o commit que introduziu um determinado problema em um projeto. Essa ferramenta utiliza uma abordagem de busca binária para encontrar o commit culpado em um histórico de commits.
Ele funciona basicamente com a analogia, dividir para conquistar, onde ele vai separando a parte boa das partes ruins até encontar o bug.

Ele pode ser usado com os seguintes comandos:

1. Primeiro precisamos pegar o primeiro commit: ` git log --oneline | tail -n 1`
2. Usar o ``git bisect start``
3. Marcar o commit ruim com `git bisect bad`
4. Marcar o commit bom ` git bisect good f0ea950`
5. Podemos visualizar o que ele está fazendo ` git bisect visualize --oneline`
6. Terminar o processo `git bisect reset`

**Dica de funcionamento**

- *Se eu marcar um commit como `bad`, ele se tornará o primeiro da lista de commits*

## Git rebase

O rebase é uma operação no Git que permite mover ou combinar commits de uma ramificação para outra. Ele reescreve o histórico de commits, aplicando as alterações de um ramo em cima de outro. O rebase é uma alternativa ao merge, que combina as alterações de diferentes ramificações criando um novo commit de merge.

![alt text](image-1.png)

*Importante: esse recurso é para ser realizado localmente e não no github*

**Comando para realizar o rebase**

````
git rebase -i [branch definida]
````

**Git amend**

git commit --amend é um comando do Git que permite adicionar mudanças ao último commit realizado. Em vez de criar um novo commit, ele combina as mudanças com o commit anterior, alterando assim o histórico de commits.

Este comando é útil quando você esquece de incluir arquivos em um commit ou deseja modificar a mensagem do commit mais recente.

````
git commit --amend

````

**Tela do git rebase**

 ````
 pick ff7a61c estou criando novos requisitos de projeto
pick 86f3085 ~definindo o padrão de projeto

# Rebase e191cad..86f3085 onto e191cad (2 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c <commit> to reword the commit message
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.

 ````


    M_M_______
  /-          \
E  0          /~~
 \           /
  ¨¨W¨¨¨¨¨W¨  

## Comandos básicos do vim

Aqui estão alguns dos principais comandos do Vim no Linux:

1. **Modo de Inserção:**
   - `i`: Inserir texto antes do cursor.
   - `a`: Inserir texto após o cursor.
   - `o`: Inserir uma nova linha abaixo da linha atual e começar a inserir texto.
   - `O`: Inserir uma nova linha acima da linha atual e começar a inserir texto.

2. **Modo Normal:**
   - `h`, `j`, `k`, `l`: Movimentar o cursor (esquerda, baixo, cima, direita).
   - `x`: Excluir o caractere sob o cursor.
   - `dd`: Excluir a linha atual.
   - `yy`: Copiar a linha atual.
   - `p`: Colar o texto copiado ou excluído após o cursor.
   - `u`: Desfazer a última operação.
   - `Ctrl + r`: Refazer a última operação desfeita.

3. **Navegação:**
   - `G`: Ir para a última linha do arquivo.
   - `gg`: Ir para a primeira linha do arquivo.
   - `:n`: Ir para a linha n (substitua "n" pelo número da linha desejada).
   - `Ctrl + u`: Rolar para cima meia página.
   - `Ctrl + d`: Rolar para baixo meia página.

4. **Salvar e Sair:**
   - `:w`: Salvar o arquivo.
   - `:q`: Sair do Vim.
   - `:q!`: Sair do Vim sem salvar as alterações.
   - `:wq` ou `:x`: Salvar e sair do Vim.

Estes são apenas alguns dos comandos básicos. O Vim é um editor muito poderoso com muitos recursos adicionais.





















