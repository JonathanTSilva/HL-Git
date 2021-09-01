# Meu CheatSheet de Git
Passo a passo que adoto na minha utilização do git.

## Instalação e Configuração
O download do Git pode ser feito pelo seguinte [LINK][1], e toda a instalação pode ser feita pelas opções *default* do instalador. Ou, no caso de um cliente Linux (Debian/Ubuntu), utilizar: `apt-get install git` (ver mais opções na [página de Linux do Git][2])

### Cmder
Uma outra opção de utilização do Git, é pelo aplicativo terceiro [Cmder][3]. Nele o git já vem instalado e basta realizar os seguintes passos para completar a configuração:
1. Ao fazer o download do arquivo .zip, extrair todo o conteúdo dentro da pasta **.cmder** no **%UserProfile%**;
2. Definir um atalho para o .exe do Cmder e enviar para o local de preferência;
3. Ao abrir o Cmder, `Ctrl + T` e criar um novo console como `{bash::mintty as Admin}` para entrar como um editor Unix. Para não ficar fazendo isso toda vez, realizar as seguintes alterações:
   * Setting > Startup > Check "Specified named task" > Choose `{bash::mintty as Admin}` > Save Settings

**Keyboard Shortcuts**:

<kbd>Ctrl</kbd>+<kbd>L</kbd> - Limpar a tela do terminal

<kbd>Ctrl</kbd>+<kbd>Ins</kbd> - Copiar

<kbd>Shift</kbd>+<kbd>Ins</kbd> - Colar

**Comandos para o vi**

<kbd>I</kbd> - Editar a janela

<kbd>:</kbd><kbd>x</kbd> or <kbd>:</kbd><kbd>w</kbd><kbd>q</kbd> - Sair do vi, gravando o arquivo modificado no arquivo nomeado na chamada original

<kbd>:</kbd><kbd>q</kbd> - Sair do vi

Para mais comandos relacionados ao editor vi, verificar esta página de [*Basic vi Commands*][4].

## Primeiros Passos:
Primeiramente, é necessário configurar o espaço do Git em seu computador, adicionando Nome e Email. Para isso, abra o terminal Unix (de sua preferência) e digíte:

```git
git --version
git config --global user.name "[NOME]"
git config --global user.email "[EMAIL]"
git config --list
```

Nos comandos acima, podemos verificar a versão instalada do git (1), configurar o nome (2) e email (3) e em seguida, verificar se os dados foram cadastrados corretamente.

Ao iniciar um projeto, deve-se mostrar para o Git que esta pasta é um repositório local:

```git
git init
dir -a
```

Ao inicializar o Git (1), é criada uma pasta oculta com o nome .git, sendo possível enxergá-la com uma opção -a para o código dir (2). Também é criada uma branch (que vem com o nome *default* `master`). Se no caso a branch padrão do GitHub estiver com outro nome, basta altrar no próprio GitHub ou alterar a do Git local com os seguintes comandos:

```git
git branch --list
git branch -m [ANTIGO] [NOVO]
git branch -a
```

A diferença entre o comando (1) e (3) é que o primeiro lista somente as *branchs* locais, já o segundo lista tanto as locais quanto remotas.







* gfp - git fetch --purse -> para ter certeza se está tudo ok, combinado remoto com local, se não, deleta no local o que não estiver no github;
* gs - git status;
* git branch - para verfificar quais as branchs do meu projeto; geralmente sempre a develop e a main (excluir com 'git branch -d NOME_DA_BRANCH' caso haja alguma desnecessária);
* git pull - para ver se tem algo a trazer do github;
* gffs estilos_login - começando agora uma nova branch de feature;
* git diff - para ver as alteraçoes feitas - ANTES DO GIT ADD
* git add .
* git commit -m 'message' -m 'optional, better description'
* Alteração antes de produzir uma release
* gfp - comando para dar uma atualizada no git
* git pull origin main --allow-unrelated-histories - é o comando para quando há erro no push

<!-- Markdown's Links -->
<!-- SITES -->
[1]: https://git-scm.com/
[2]: https://git-scm.com/download/linux
[3]: https://cmder.net/
[4]: https://www.cs.colostate.edu/helpdocs/vi.html