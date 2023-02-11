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
