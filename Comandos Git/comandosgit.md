Lista Comandos Git :desktop_computer:

> *Essa lista foi criada para que eu possa desenvolver meus estudos no Git iniciado aqui na [DIO](https://www.dio.me/), resolvi fazer uma lista com comandos do Git, de forma que fixe o meu aprendizado e caso apareça dúvidas eu tenha um local de referencia de estudo*.
Lembrando que para maiores detalhes, dos comandos basta consultar a documentação ( [Site GIT](https://git-scm.com/docs/git/pt_BR) ) ou o velho amigo Google:slightly_smiling_face:



### Estados

- Modificado (modified);
- Preparado (staged/index)
- Consolidado (comitted);

### Ajuda

- Geral

##### GERAL

```
git help
```

##### COMANDO ESPECÍFICO

```
git help add
git help commit
git help <qualquer_comando_git>
```



## Configuração

### Geral

As configurações do GIT são armazenadas no arquivo **.gitconfig** localizado dentro do diretório do usuário do Sistema Operacional (Ex.: Windows: C:\Users\Documents and Settings\Leonardo ou *nix /home/leonardo).



As configurações realizadas através dos comandos abaixo serão incluídas no arquivo citado acima.

##### SETAR USUÁRIO

```
git config --global user.name "Leonardo Comelli"
```

##### SETAR EMAIL

```
git config --global user.email leonardo@software-ltda.com.br
```

##### SETAR EDITOR

```
git config --global core.editor vim
```

##### SETAR FERRAMENTA DE MERGE

```
git config --global merge.tool vimdiff
```

##### SETAR ARQUIVOS A SEREM IGNORADOS

```
git config --global core.excludesfile ~/.gitignore
```

##### LISTAR CONFIGURAÇÕES

```
git config --list
```

### Ignorar Arquivos

Os nomes de arquivos/diretórios ou extensões de arquivos listados no arquivo **.gitignore** não serão adicionados em um repositório. Existem dois arquivos .gitignore, são eles:

- Geral: Normalmente armazenado no diretório do usuário do Sistema Operacional. O arquivo que possui a lista dos arquivos/diretórios a serem ignorados por **todos os repositórios** deverá ser declarado conforme citado acima. O arquivo não precisa ter o nome de **.gitignore**.
- Por repositório: Deve ser armazenado no diretório do repositório e deve conter a lista dos arquivos/diretórios que devem ser ignorados apenas para o repositório específico.

## Repositório Local

### Criar novo repositório

```
git init
```

### Verificar estado dos arquivos/diretórios

```
git status
```

### Adicionar arquivo/diretório (staged area)

##### ADICIONAR UM ARQUIVO EM ESPECÍFICO

```
git add meu_arquivo.txt
```

##### ADICIONAR UM DIRETÓRIO EM ESPECÍFICO

```
git add meu_diretorio
```

##### ADICIONAR TODOS OS ARQUIVOS/DIRETÓRIOS

```
git add .	
```

##### ADICIONAR UM ARQUIVO QUE ESTA LISTADO NO .GITIGNORE (GERAL OU DO REPOSITÓRIO)

```
git add -f arquivo_no_gitignore.txt
```

### Comitar arquivo/diretório

##### COMITAR UM ARQUIVO

```
git commit meu_arquivo.txt
```

##### COMITAR VÁRIOS ARQUIVOS

```
git commit meu_arquivo.txt meu_outro_arquivo.txt
```

##### COMITAR INFORMANDO MENSAGEM

```
git commit meuarquivo.txt -m "minha mensagem de commit"
```

### Remover arquivo/diretório

##### REMOVER ARQUIVO

```
git rm meu_arquivo.txt
```

##### REMOVER DIRETÓRIO

```
git rm -r diretorio
```

### Visualizar hitórico

##### EXIBIR HISTÓRICO

```
git log
```

##### EXIBIR HISTÓRICO COM DIFF DAS DUAS ÚLTIMAS ALTERAÇÕES

```
git log -p -2
```

##### EXIBIR RESUMO DO HISTÓRICO (HASH COMPLETA, AUTOR, DATA, COMENTÁRIO E QTDE DE ALTERAÇÕES (+/-))

```
git log --stat
```

##### EXIBIR INFORMAÇÕES RESUMIDAS EM UMA LINHA (HASH COMPLETA E COMENTÁRIO)

```
git log --pretty=oneline
```

##### EXIBIR HISTÓRICO COM FORMATAÇÃO ESPECÍFICA (HASH ABREVIADA, AUTOR, DATA E COMENTÁRIO)

```
git log --pretty=format:"%h - %an, %ar : %s"
```

- %h: Abreviação do hash;
- %an: Nome do autor;
- %ar: Data;
- %s: Comentário.

Verifique as demais opções de formatação no [Git Book](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History)

##### EXIBIR HISTÓRIO DE UM ARQUIVO ESPECÍFICO

```
git log -- <caminho_do_arquivo>
```

##### EXIBIR HISTÓRICO DE UM ARQUIVO ESPECÍFICO QUE CONTÊM UMA DETERMINADA PALAVRA

```
git log --summary -S<palavra> [<caminho_do_arquivo>]
```

##### EXIBIR HISTÓRICO MODIFICAÇÃO DE UM ARQUIVO

```
git log --diff-filter=M -- <caminho_do_arquivo>
```

- O pode ser substituido por: Adicionado (A), Copiado (C), Apagado (D), Modificado (M), Renomeado (R), entre outros.

##### EXIBIR HISTÓRIO DE UM DETERMINADO AUTOR

```
git log --author=usuario
```

##### EXIBIR REVISÃO E AUTOR DA ÚLTIMA MODIFICAÇÃO DE UMA BLOCO DE LINHAS

```
git blame -L 12,22 meu_arquivo.txt 
```

### Desfazendo operações

##### DESFAZENDO ALTERAÇÃO LOCAL (WORKING DIRECTORY)

Este comando deve ser utilizando enquanto o arquivo não foi adicionado na **staged area**.

```
git checkout -- meu_arquivo.txt
```

##### DESFAZENDO ALTERAÇÃO LOCAL (STAGING AREA)

Este comando deve ser utilizando quando o arquivo já foi adicionado na **staged area**.

```
git reset HEAD meu_arquivo.txt
```

Se o resultado abaixo for exibido, o comando reset *não* alterou o diretório de trabalho.

```
Unstaged changes after reset:
M	meu_arquivo.txt
```

A alteração do diretório pode ser realizada através do comando abaixo:

```
git checkout meu_arquivo.txt
```

## Repositório Remoto

### Exibir os repositórios remotos

```
git remote
git remote -v
```

### Vincular repositório local com um repositório remoto

```
git remote add origin git@github.com:leocomelli/curso-git.git
```

### Exibir informações dos repositórios remotos

```
git remote show origin
```

### Renomear um repositório remoto

```
git remote rename origin curso-git
```

### Desvincular um repositório remoto

```
git remote rm curso-git
```

### Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

```
git push -u origin master
```



Os demais **pushes** não precisam dessa informação

```
git push
```

### Atualizar repositório local de acordo com o repositório remoto

##### ATUALIZAR OS ARQUIVOS NO BRANCH ATUAL

```
git pull
```

##### BUSCAR AS ALTERAÇÕES, MAS NÃO APLICA-LAS NO BRANCH ATUAL

```
git fecth
```

### Clonar um repositório remoto já existente

```
git clone git@github.com:leocomelli/curso-git.git
```

### Tags

##### CRIANDO UMA TAG LEVE

```
git tag vs-1.1
```

##### CRIANDO UMA TAG ANOTADA

```
git tag -a vs-1.1 -m "Minha versão 1.1"
```

##### CRIANDO UMA TAG ASSINADA



Para criar uma tag assinada é necessário uma chave privada (GNU Privacy Guard – GPG).

```
git tag -s vs-1.1 -m "Minha tag assinada 1.1"
```

##### CRIANDO TAG A PARTIR DE UM COMMIT (HASH)

```
git tag -a vs-1.2 9fceb02
```

##### CRIANDO TAGS NO REPOSITÓRIO REMOTO

```
git push origin vs-1.2
```

##### CRIANDO TODAS AS TAGS LOCAIS NO REPOSITÓRIO REMOTO

```
git push origin --tags
```

### Branches

O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro *especial* que indica qual é o branch atual. Por padrão, o **HEAD** aponta para o branch principal, o **master**.

##### CRIANDO UM NOVO BRANCH

```
git branch bug-123
```

##### TROCANDO PARA UM BRANCH EXISTENTE

```
git checkout bug-123
```



Neste caso, o ponteiro principal **HEAD** esta apontando para o branch chamado bug-123.

##### CRIAR UM NOVO BRANCH E TROCAR

```
git checkout -b bug-456
```

##### VOLTAR PARA O BRANCH PRINCIPAL (MASTER)

```
git checkout master
```

##### RESOLVER MERGE ENTRE OS BRANCHES

```
git merge bug-123
```

Para realizar o *merge*, é necessário estar no branch que deverá receber as alterações. O *merge* pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

A mensagem indicando um *merge* manual será:

```
Automerging meu_arquivo.txt
CONFLICT (content): Merge conflict in meu_arquivo.txt
Automatic merge failed; fix conflicts and then commit the result.
```

##### APAGANDO UM BRANCH

```
git branch -d bug-123
```

##### LISTAR BRANCHES

###### LISTAR BRANCHES

```
git branch
```

###### LISTAR BRANCHES COM INFORMAÇÕES DOS ÚLTIMOS COMMITS

```
git branch -v
```

###### LISTAR BRANCHES QUE JÁ FORAM FUNDIDOS (MERGED) COM O **MASTER**

```
git branch --merged
```

###### LISTAR BRANCHES QUE NÃO FORAM FUNDIDOS (MERGED) COM O **MASTER**

```
git branch --no-merged
```

##### CRIANDO BRANCHES NO REPOSITÓRIO REMOTO

###### CRIANDO UM BRANCH REMOTO COM O MESMO NOME

```
git push origin bug-123
```

###### CRIANDO UM BRANCH REMOTO COM NOME DIFERENTE

```
git push origin bug-123:new-branch
```

##### BAIXAR UM BRANCH REMOTO PARA EDIÇÃO

```
git checkout -b bug-123 origin/bug-123
```

##### APAGAR BRANCH REMOTO

```
git push origin:bug-123
```

### Rebasing

Fazendo o **rebase** entre um o branch bug-123 e o master.

```
git checkout experiment
git rebase master
```



Mais informações e explicações sobre o [Rebasing](http://git-scm.com/book/en/Git-Branching-Rebasing)

### Stash

Para alternar entre um branch e outro é necessário fazer o commit das alterações atuais para depois trocar para um outro branch. Se existir a necessidade de realizar a troca sem fazer o commit é possível criar um **stash**. O Stash como se fosse um branch temporário que contem apenas as alterações ainda não commitadas.

##### CRIAR UM STASH

```
git stash
```

##### LISTAR STASHES

```
git stash list
```

##### VOLTAR PARA O ÚLTIMO STASH

```
git stash apply
```

##### VOLTAR PARA UM STASH ESPECÍFICO

```
git stash apply stash@{2}
```

Onde **2** é o indíce do stash desejado.

##### CRIAR UM BRANCH A PARTIR DE UM STASH

```
git stash branch meu_branch
```

### Reescrevendo o histórico

##### ALTERANDO MENSAGENS DE COMMIT

```
git commit --amend -m "Minha nova mensagem"
```

##### ALTERAR ÚLTIMOS COMMITS

Alterando os três últimos commits

```
git rebase -i HEAD~3
```

O editor de texto será aberto com as linhas representando os três últimos commits.

```
pick f7f3f6d changed my name a bit
pick 310154e updated README formatting and added blame
pick a5f4a0d added catfile
```

Altere para edit os commits que deseja realizar alterações.

```
edit f7f3f6d changed my name a bit
pick 310154e updated README formatting and added blame
pick a5f4a0d added catfile
```

Feche o editor de texto.

Digite o comando para alterar a mensagem do commit que foi marcado como *edit*.

```
git commit –amend -m “Nova mensagem”
```

Aplique a alteração

```
git rebase --continue
```



**Atenção:** É possível alterar a ordem dos commits ou remover um commit apenas mudando as linhas ou removendo.

##### JUNTANDO VÁRIOS COMMITS

Seguir os mesmos passos acima, porém marcar os commtis que devem ser juntados com **squash*

##### REMOVER TODO HISTÓRICO DE UM ARQUIVO

```
git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
```

### Bisect

O bisect (pesquisa binária) é útil para encontrar um commit que esta gerando um bug ou uma inconsistência entre uma sequência de commits.

##### INICIAR PEQUINSA BINÁRIA

```
git bisect start
```

##### MARCAR O COMMIT ATUAL COMO RUIM

```
git bisect bad
```

##### MARCAR O COMMIT DE UMA TAG QUE ESTA SEM O BUG/INCONSISTÊNCIA

```
git bisect good vs-1.1
```

##### MARCAR O COMMIT COMO BOM



O GIT irá navegar entre os commits para ajudar a indentificar o commit que esta com o problema. Se o commit atual não estiver quebrado, então é necessário marca-lo como **bom**.

```
git bisect good
```

##### MARCAR O COMMIT COMO RUIM

Se o commit estiver com o problema, então ele deverá ser marcado como **ruim**.

```
git bisect bad
```

##### FINALIZAR A PESQUISA BINÁRIA

Depois de encontrar o commit com problema, para retornar para o *HEAD* utilize:

```
git bisect reset
```
 16  
