# Manual - Git
Colocarei aqui um passo a passo que adoto na minha utilização do git.

## Instalação
O download do Git pode ser feito pelo seguinte link: https://git-scm.com/ e toda a instalação pode ser feita pelas opções ~default~ do instalador.

Uma outra opção de utilização do Git, é pelo aplicativo terceiro Cmder. Nele o git já vem instalado e basta realizar os seguintes passos para completar a configuração:

## Começando projeto do zero:

* gfp - git fetch --purse -> para ter certeza se está tudo ok, combinado remoto com local, se não, deleta no local o que não estiver no github;
* gs - git status;
* git branch - para verfificar quais as branchs do meu projeto; geralmente sempre a develop e a main (excluir com 'git branch -d NOME_DA_BRANCH' caso haja alguma desnecessária);
* git pull - para ver se tem algo a trazer do github;
* gffs estilos_login - começando agora uma nova branch de feature;
* git diff - para ver as alteraçoes feitas - ANTES DO GIT ADD
* git add .
* git commit -m 'message' -m 'optional, better description'
* 
* Alteração antes de produzir uma release
* gfp - comando para dar uma atualizada no git
* git pull origin main --allow-unrelated-histories - é o comando para quando há erro no push
