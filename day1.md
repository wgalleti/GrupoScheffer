# Treinamentos Internos - TI

## Dia 1 - Controle de Versão

Nessa etapa vamos enteder o que é um controle de Versão, e algumas funcionalidades básicas para iniciar sua utilização.

### O que é GIT?

*Git pronunciado [guit] é um sistema de controle de versão distribuído e um sistema de gerenciamento de código fonte, com ênfase em velocidade. O Git foi inicialmente projetado e desenvolvido por Linus Torvalds para o desenvolvimento do kernel Linux, mas foi adotado por muitos outros projetos.*

[Wikipedia](https://pt.wikipedia.org/wiki/Git)

### O que já existe?

Repósitórios online:  
[Github](http://github.com)  
*Gratuito para repositórios públicos, mais utilizado*
[Gitlab](http://gitlab.com)  
*Gratuito para repositórios públicos e privados, sem limites de projetos ˆˆ*
[Bitbucket](http://bitbucket.org/)
*Gratuito para repositórios públicos, com limite de 10 repositórios privados*

### Como usar?!

Para interagir com nossos servidores, vamos utilizar a ferramenta [git-scm](https://git-scm.com/) para executar nossas tarefas de controle de versão.

***Atente aos detalhes de instalação***

Lembrando que é necessário definir suas credênciais. Vamos utilizar os seguintes comandos:

```git
git config --global user.name "William Galleti"
git config --global user.email "william.galleti@gmail.com"
```

Após isso, é necessário avisar para o servidor, que você esta trabalhando com ele e que tem permissão. Essa permissão é feita através de um ssh com algoritimo RSA (duas etapas). O gitlab tem um [manualzinho](https://gitlab.com/help/ssh/README) bem legal de como adicionar essa permissão ssh

### Como funciona?!

O Git funciona como *Fluxo de trabalho*

Seus repositórios locais consistem em três "árvores" mantidas pelo git.  
A primeira delas é sua Working Directory que contém os arquivos vigentes.  
A segunda Index que funciona como uma área temporária e finalmente a HEAD que aponta para o último commit (confirmação) que você fez.

##### Iniciando o git

A primeira etapa para utilização do git, é você definir o seu Working Directory. Para isso existem várias formas. Vamos as duas principais:

Para novos projetos, onde você ira iniciar e enviar os arquivos locais existentes para um repositório vazio, vamos utilizar os seguintes comandos:

```git
git init
git add remote origin seurepositorio
```

Para projetos que já existem no servidor, você ira utilizar os seguintes comandos:

```git
git clone seurepositorio
```

##### Adicionando arquivos

O primeiro comando que precisamos utilizar é para adicionar arquivos ao seu WorkTree. O comando git é `git add`. Vamos aos exemplos:

Adicionar o arquivo `readme.md` : `git add readme.md`  
Adicionar todos arquivos `php` : `git add .php`  
Adicionar todos os `arquivos` : `git add .`  

##### Commitando as alterações

Após adicionar os arquivos, precisamos informar as alterações, issues, mensagens que eles sofreram. Para isso vamos utilizar o comando `git commit`. Vamos aos exemplos:

Enviando o primeiro commit: `git commit -m "Primeiro commit"`  
Enviando commit de correção de issue: `git commit -m "Corrigindo bug #numero da issue"`  

##### Enviando as alteações para o servidor

Após definir seus commits, precisamos enviar os mesmos para o servidor. Para isso utilizamos o comando `git push`

Comando padrão para enviar `git push -u origin SEUBRANCH`

*o parâmetro -u indica o usuário que está no git config*
*o paramentro origin indica que irá para a origem no proximo parâmetro*
*SEUBRANCH indica o branch que você esta trabalhando*


#### WTF is branch?

Um branch no Git é simplesmente um leve ponteiro móvel para um desses commits. O nome do branch padrão no Git é master. Como você inicialmente fez commits, você tem um branch principal ( master branch ) que aponta para o último commit que você fez. Cada vez que você faz um commit ele avança automaticamente.

**Tá mais e ai?!**

Resumindo, o branch é uma posição do seu fonte. Por padrão, o branch do git é o `master`. Vamos ao exemplo, que você irá efetuar uma mudança no seu projeto, para adicionar uma nova funcionalidade. Podemos efetuar uma cópia do branch `master` para o novo branch `funcionalidade` e todas as alterações, serão efetuadas no `funcionalidade`, mantendo o `master` como estava.

##### Trabalhando com branch

O fluxo do branch que não seja o `master` segue a seguinte regra.

1. Criar o branch
2. Efetuar os commits
3. Efetuar o merge
4. Remover o branch


###### Criando um branch

`git checkout -b NOMEDOBRANCH`

Com esse comando, o git irá efetuar uma copía do branch atual que você esta para o branch `NOMEDOBRANCH` e já irá definir o seu novo branch como ativo.

###### Efetuando merge

```git
git checkout master
git merge NOMEDOBRANCH
```

Para efetuar um merge, precisamos voltar ao branch que queremos unir as alterações através do `git checkout` e chamar o comando merge passando como parametro o nome do branch que queremos que sejá unificado.

###### Removendo branch

`git branch -d NOMEDOBRANCH`

Após efetuar o merge, caso o branch não sejá mais necessário, podemos chamar o comando `git branch` passando o parametro `-d` para deletar e o nome do branch a ser deletado


### Bonus

`git status` : lista a situação do seu repositório
`git pull` : Recebe as alterações para o seu repositório

#### Fontes
[http://rogerdudler.github.io/git-guide/index.pt_BR.html](http://rogerdudler.github.io/git-guide/index.pt_BR.html)  
[Primeiros passos](https://git-scm.com/book/pt-br/v1/Primeiros-passos-No%C3%A7%C3%B5es-B%C3%A1sicas-de-Git)  