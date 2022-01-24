<!-- Simple logo -->
<a href="#meu-guia-de-git"><img width="400px" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT-gtjD0wp0QJuTGvA0pjHgFYgWPmzb92tu-w&usqp=CAU" align="right" /></a>

# Meu guia de Git

🛠 Passo a passo que adoto na minha utilização do git.

- [Meu CheatSheet de Git](#meu-cheatsheet-de-git)
  - [1. Instalação e Configuração](#1-instalação-e-configuração)
    - [1.1. Visual Studio Code](#11-visual-studio-code)
    - [1.2. Cmder](#12-cmder)
      - [1.2.1. Keyboard Shortcuts](#121-keyboard-shortcuts)
      - [1.2.2. Comandos para o vi](#122-comandos-para-o-vi)
  - [2. Primeiros Passos](#2-primeiros-passos)
  - [3. Comunicação com remotos (GitHub, BitBucket, GitLab)](#3-comunicação-com-remotos-github-bitbucket-gitlab)
    - [3.1. Criando chave SSH](#31-criando-chave-ssh)
      - [3.1.1. PuTTY](#311-putty)
      - [3.1.2. Linha de comando](#312-linha-de-comando)
    - [3.2. Cruzando chave SSH](#32-cruzando-chave-ssh)
    - [3.3. Configuração com Proxy](#33-configuração-com-proxy)
  - [4. Comandos Básicos](#4-comandos-básicos)
    - [4.1. Clonando Repositórios](#41-clonando-repositórios)
  - [5. Comandos Intermediários e Avançados](#5-comandos-intermediários-e-avançados)
    - [5.1. Enviando Branch para Remoto](#51-enviando-branch-para-remoto)
    - [5.2. Atualizando Branch Local com o Remoto](#52-atualizando-branch-local-com-o-remoto)
    - [5.3. Deletando Branch do Remoto](#53-deletando-branch-do-remoto)
    - [5.4. Renomeando uma Branch](#54-renomeando-uma-branch)
    - [5.5. Mesclando Alterações](#55-mesclando-alterações)
    - [5.6. Resolvendo Conflitos](#56-resolvendo-conflitos)
    - [5.7. Pull Request](#57-pull-request)
    - [5.8. Criando e Listando Tags](#58-criando-e-listando-tags)
      - [5.8.1. *Semantic Versioning*](#581-semantic-versioning)
    - [5.9. Stash](#59-stash)
    - [5.10. CherryPick](#510-cherrypick)
    - [5.11. Rebase](#511-rebase)
  - [6. Mensagens de Erro, Workarounds e Dicas](#6-mensagens-de-erro-workarounds-e-dicas)
    - [6.1. Alterações Não Versionadas](#61-alterações-não-versionadas)
    - [6.2. Desfazendo Commits](#62-desfazendo-commits)
    - [6.3. Padronizando Commits](#63-padronizando-commits)
  - [7. Utilidades](#7-utilidades)
    - [7.1. GitFlow](#71-gitflow)
    - [7.2. Alias](#72-alias)
      - [7.2.1. Minhas Aliases](#721-minhas-aliases)
    - [7.3. Grep](#73-grep)
  - [8. Ferramentas Gráficas](#8-ferramentas-gráficas)
    - [8.1. kdiff3](#81-kdiff3)
      - [8.2. Sourcetree](#82-sourcetree)
      - [8.3. GitKraken](#83-gitkraken)

## 1. Instalação e Configuração

O download do Git pode ser feito pelo seguinte [LINK][1], e toda a instalação pode ser feita pelas opções *default* do instalador. Ou, no caso de um cliente Linux (Debian/Ubuntu), utilizar: `apt-get install git` (ver mais opções na [página de Linux do Git][2]). Vale ressaltar um ponto importante na instalação do Git que é a opção de "Adding Git-Bash to the new Windows Terminal"; este novo terminal do windows agrupa as ferramentas e shells de linha de comando, como prompt de comando, PowerShell, WSL e GitBash, caso marque a opção na instalação do Git. O download pode ser feito na Microsoft Store ou pelo seguinte [link][8].

Fica a dica de uma aplicação desenvolvida para uma melhor visualização de como funciona o Git, ou até mesmo, uma ferramenta para criar imagens para didática do Git: [Git-School][10].

![git-school][git-school]

### 1.1. Visual Studio Code

O VSCode é o editor de código-fonte mais utilizado do mundo. Uma de suas principais vantagens frente à outros editores é a utilização de extensões desenvolvidas pela comunidade, que inclui suporte para depuração, controle de versionamento Git incorporado (*Source Control*), realce de sintaxe, complementação inteligente de código, snippets e refatoração de código.. Neste tópico serão abordadas as melhores extensões para utilizar o Git com o VSCode da melhor forma e aproveitando os melhores recursos que o editor tem a oferecer.

Um detalhe a acrescentar para este tópico a possibilidade de uma pasta `.vscode/` que contenha as informações específicas para esta integração, como um arquivo `extensions.json` que carrega as extensões recomendadas para uma melhor utilização de um determinado *workspace* (repositório):

```json
{
    "recommendations": [
        "ms-ceintl.vscode-language-pack-pt-br"
    ]
}
```

Para mais dicas de instalação, teclas de atalho, plugins e integrações, ver material de apoio [1][9].

**Source Control** <br>
O Visual Studio Code integrou o gerenciamento de controle de origem (SCM) e inclui suporte Git pronto para uso. Muitos outros provedores de controle de origem estão disponíveis por meio de extensões no VS Code Marketplace.

É esta função nativa que habilita os seguintes marcadores de estado dos arquivos:

- **A** - Added (Este é um arquivo novo que foi adicionado ao seu repositório)
- **M** - Modified (Um arquivo existente que foi alterado)
- **D** - Deleted (Um arquivo foi excluido)
- **U** - Untracked (O arquivo é novo ou foi alterado, mas ainda não foi adicionado ao repositório)
- **C** - Conflict (Há um conflito no arquivo)
- **R** - Renamed (O arquivo foi renomeado)
- **S** - Submodule (No repositório, existe outro sub-repositório)

**Git Lens** <br>
O GitLens sobrecarrega os recursos do Git integrados ao Visual Studio Code. Ele ajuda você a visualizar a autoria do código rapidamente por meio de anotações de culpa do Git e lentes de código, navegar e explorar repositórios Git perfeitamente, obter insights valiosos por meio de comandos de comparação poderosos e muito mais.

**Git History** <br>
Ver git log, histórico de arquivos, comparar branches ou commits

**Git Graph** <br>
Visualize um gráfico Git de seu repositório e execute facilmente ações Git a partir do gráfico. Configurável para ter a aparência que você deseja!

### 1.2. Cmder

Uma outra opção de utilização do Git, é pelo aplicativo terceiro [Cmder][3]. Nele o git já vem instalado e basta realizar os seguintes passos para completar a configuração:

1. Ao fazer o download do arquivo .zip, extrair todo o conteúdo dentro da pasta **.cmder** no **%UserProfile%**;
2. Definir um atalho para o .exe do Cmder e enviar para o local de preferência;
3. Ao abrir o Cmder, `Ctrl + T` e criar um novo console como `{bash::mintty as Admin}` para entrar como um editor Unix. Para não ficar fazendo isso toda vez, realizar as seguintes alterações:
   - <kbd>Settings</kbd> > <kbd>Startup</kbd> > Check "Specified named task" > Choose <kbd>{bash::mintty as Admin}</kbd> > <kbd>Save Settings</kbd>

#### 1.2.1. Keyboard Shortcuts

<kbd>Ctrl</kbd>+<kbd>L</kbd> - Limpar a tela do terminal

<kbd>Ctrl</kbd>+<kbd>Ins</kbd> - Copiar

<kbd>Shift</kbd>+<kbd>Ins</kbd> - Colar

#### 1.2.2. Comandos para o vi

<kbd>I</kbd> - Editar a janela

<kbd>:</kbd><kbd>x</kbd> or <kbd>:</kbd><kbd>w</kbd><kbd>q</kbd> - Sair do vi, gravando o arquivo modificado no arquivo nomeado na chamada original

<kbd>:</kbd><kbd>q</kbd> - Sair do vi

Para mais comandos relacionados ao editor vi, verificar esta página de [*Basic vi Commands*][4].

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 2. Primeiros Passos

Primeiramente, é necessário configurar o espaço do Git em seu computador, adicionando Nome e Email. Para isso, abra o terminal Unix (de sua preferência) e digite:

```cmd
(1) λ git --version
(2) λ git config --global user.name "[NOME]"
(3) λ git config --global user.email "[EMAIL]"
(4) λ git config --list
```

Nos comandos acima, podemos verificar a versão instalada do git (1), configurar o nome (2) e email (3) e em seguida, verificar se os dados foram cadastrados corretamente.

Ao iniciar um projeto, deve-se mostrar para o Git que esta pasta é um repositório local:

```cmd
(5) λ git init
(6) λ dir -a
(7) λ ls
```

Para adicionar um repositório remoto à uma pasta já existente localmente, linkar o remoto com (8):

```cmd
(8) λ git remote add origin [LINKSSH]
```

Ao inicializar o Git (5), é criada uma pasta oculta com o nome .git, sendo possível enxergá-la com uma opção -a para o código dir (6) ou utilizar o (7). Também é criada uma branch (que vem com o nome *default* `master`). Se no caso a branch padrão do GitHub estiver com outro nome, basta alterar no próprio GitHub ou alterar a do Git local com os seguintes comandos:

```cmd
(9.1) λ git branch
(9.2) λ git branch --list
(9.3) λ git branch -m [ANTIGO] [NOVO]
(9.4) λ git branch -a
```

A diferença entre o comando (8.1/8.2) e (8.4) é que o primeiro lista somente as *branchs* locais, já o segundo lista tanto as locais quanto remotas.

Para excluir uma branch local:

```cmd
(9.5) λ git branch -d [BRANCH]
(9.6) λ git branch -D [BRANCH]
```

Utilizar (8.5) para apagar somente a branch se você já tiver feito merge ou enviado as alterações para seu repositório remoto, evitando perda de código, ou (8.6), para ignorar o estado da sua branch, forçando a sua remoção. Vale ressaltar que não é possível realizar esta alteração se estiver `checkout` na branch. Mas se por acaso se arrependa da remoção indevida da branch, basta trazê-la de novo ao local por `git checkout [BRANCH]`.

Caso queira deletar por completo algum repositório criado localmente pelo `git init`:

```cmd
(10) λ rm -rf .git
```

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 3. Comunicação com remotos (GitHub, BitBucket, GitLab)

Para realizar a comunicação entre o Git local e aplicações remotas é necessária uma configuração de segurança através de SSH. É possível também comunicar local com remoto sem o SSH, entretanto, toda vez que precisar fazer um *push* no remoto, solicitará a senha para do usuário, verificando se o repositório em questão é seu.

### 3.1. Criando chave SSH

O SSH (*Secure Shell* ou *Secure Socket Shell*) é um protocolo que permite a conexão com servidores remotos, de forma criptografada e mais segura, usando um par de chaves (RSA, DSA...). Há duas principais formas de criarmos essa chave: utiliazando um software terceiro - PuTTY, ou criando por linha de comando.

Primeiramente, deve-se criar uma pasta do **%UserProfile%** denominada **.ssh**, na qual guardará todas as chaves do usuário. É recomendado apenas uma de cada. Para verificar se você já tem alguma chave cadastrada, dê o seguinte comando em seu Git Bash:

```cmd
(11) λ ls -al ~/.ssh
```

Também é possível criar uma chave de segurança de hardware para que cada vez que utilizar uma máquina diferente, não precise gerar outras chaves. Entretanto, é necessário ter o hardware para este tipo de chave.

#### 3.1.1. PuTTY

1. Fazer o download do [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html), ou o programa completo, ou apenas o puttygen.exe
2. Ao entrar no PuTTY Key Generator, realizar os seguintes passos:
   - <kbd>Generate</kbd> > Mexer o mouse pela tela, pois a geração ocorre de acordo com esses movimentos > Colocar a senha e confirmar a senha > <kbd>Save public key</kbd> (com o nome `id_rsa.pub`) > <kbd>Save private key</kbd> (com o nome `id_rsa`)
   - **OBSERVAÇÕES:**
     - Essas duas chaves devem estar dentro da pasta **.ssh** criada anteriormente;
     - Pode ser que as chaves criadas pelo PuTTYgen não seja reconhecida pelas aplicações remotas como GitHub, BitBucket. Assim, é necessária conversão da mesma para OpenSSH (no próprio programa).

#### 3.1.2. Linha de comando

Cole o texto abaixo, substituindo o endereço de e-mail pelo seu GitHub.

```cmd
(12.1) λ ssh-keygen -t rsa -b 2048 -C "[EMAIL]"
```

Você pode optar por outro algoritmo como o Ed25519:

```cmd
(12.2) λ ssh-keygen -t ed25519 -C "your_email@example.com"
```

Caso queira simplificar, apenas o comando abaixo realizará o trabalho:

```cmd
(12.3) λ ssh-keygen
(12.4) λ ssh-keygen -t rsa
```

Esses comandos criaram uma nova chave SSH, usando o e-mail fornecido como uma etiqueta. Quando aparecer a solicitação "Enter a file in which to save the key" (Insira um arquivo no qual salvar a chave), pressione Enter. O local padrão do arquivo será aceito. Em seguida, digite uma frase secreta segura para essa senha gerada.

No próximo tópico, será mostrado um código .bash que adiciona a chave criada ao `ssh-agent`, mas caso queira inseri-la manualmente, seguir os códigos abaixo:

```cmd
(13) λ eval "$(ssh-agent -s)"
> Agent pid 59566
(14.1) λ ssh-add -l
(14.2) λ ssh-add ~/.ssh/[KEY]
```

O comando (14.1) listará as chaves privadas atuais disponíveis.

O `ssh-agent` retorna comandos para definir certas variáveis de ambiente no shell. Os comandos de saída por padrão são compatíveis com `/bin/sh` e `/bin/bash`. Para gerar comandos para o C-shell (`/bin/csh` ou `/bin/tcsh`), adicione a opção `-c`.

A maneira mais fácil de verificar é ver o valor da variável de ambiente `SSH_AGENT_SOCK`. Se estiver definido, o agente está presumidamente rodando. Isso pode ser verificado com:

```cmd
echo $SSH_AGENT_SOCK
```

Além disso, para permitir logins baseados em chave para servidores, a autenticação de chave pública deve ser habilitada no servidor. No **OpenSSH**, já está habilitado por padrão e é controlado pela opção **PubkeyAuthentication** em `sshd_config`.

Caso decida sair do agente, entre com o comando:

```cmd
kill $SSH_AGENT_PID
```

### 3.2. Cruzando chave SSH

Após criada a chave SSH, é necessário avisar para a sua conta do GitHub qual é o usuário (chave SSH) que ele pode confiar edição. Para isso, vá até sua conta no GitHub e siga os seguintes passos:

- <kbd>Settings</kbd> > <kbd>SSH and GPG keys</kbd> > <kbd>New SSH key</kbd> > Coloca o título de preferência e cole todo o conteúdo da chave pública gerada no campo key

Deve-se avisar também ao cliente remoto uma forma de como autenticar a sua chave local. Uma das que mais facilitam essa autenticação é a criação de um arquivo `.bashrc`, assim, sempre que o Cmder ou outro edito de texto for aberto, pedirá sua senha da chave privada para que haja a conexão.

Abaixo está um exemplo de um `.bashrc` utilizado com variáveis Alias:

```bash
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_load_env
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env

# Aliases
alias gs='git status'

```

Este arquivo deve ser colocado na pasta raiz do usuário (**%UserProfile%**) e rodado uma única vez para que crie os outros arquivos necessários.

Na maioria dos sistemas Linux, o `ssh-agent` é configurado e executado ao início do sistema automaticamente, e nenhumam ação adicional é necessária para sua utilização. No entanto, uma chave SSH ainda deve ser criada pelo usuário (vide [3.1 - Criando chave SSH](#31-criando-chave-ssh)). Se o `ssh-agent` não iniciar automaticamente no login, realizar os passos apresentados em [3.1.2. - Criando chave SSH](#31-criando-chave-ssh):


### 3.3. Configuração com Proxy

Caso o seu repositório local esteja em uma máquina na rede com proxy ou firewall e aconteça alguns problemas, é necessário configurar o git para aquele proxy, login e usuário, com os comando abaixo:

```cmd
(15) λ git config --global http.proxy http://proxyuser:proxypwd@proxy.server.com:8080
```

É necessário alterar `proxyuser` para o seu usuário do proxy, `proxypwd` para a senha do usuário, `proxy.server.com` para o server e `8080` para a porta configurada.

Em alguns casos o https também deve ser configurado. Se mesmo realizando a etapa acima não resolver, é necessário adicionar a chave manualmente na config do git seguindo os passos deste [LINK][6]

```cmd
$ ssh -Tv git@bitbucket.org
OpenSSH_6.9p1, LibreSSL 2.1.8
...
Permission denied (publickey).

$ ssh-add -l 
2048 SHA256:... /Users/user/.ssh/id_rsa (RSA)

$ ssh-add ~/.ssh/user-Bitbucket
Enter passphrase for /Users/user/.ssh/user-Bitbucket: 
Identity added: /Users/user/.ssh/user-Bitbucket (/Users/user/.ssh/user-Bitbucket)

$ ssh-add -l 
2048 SHA256:... /Users/user/.ssh/id_rsa (RSA)
2048 SHA256:... /Users/user/.ssh/user-Bitbucket (RSA)

$ ssh -Tv git@bitbucket.org
OpenSSH_6.9p1, LibreSSL 2.1.8
...
logged in as user.
```

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 4. Comandos Básicos

Ao criar o seu repositório local de trabalho e iniciar o seu Git (como visto na seção [Primeiros Passos](#primeiros-passos)), inicia-se os trabalhos neste repositório e os comandos básicos para manuseio do mesmo são:

```cmd
(16) λ git status
(17) λ git add [ARQUIVO]
(18) λ git commit -m "[MSG]"
```

Quando é realizada alguma alteração nos arquivos, ao dar o (15), será mostrado todos aqueles arquivos que estão diferentes do Git local. Atenção às cores: quando estiverem vermelhos é porque não foi passado para o Git quais arquivos devem ser *staged* (fica na *Staging Area*). Caso queria adicionar todos os arquivos (16), adicionar `git add --all` ou `git add .` ou `git add -A`. Uma outra observação válida é sobre adicionar outra sub-mensagem ao commit (17) com uma outra opção `-m "MSG"` resultando em `git commit -m "[MSG1]" -m "[MSG2]"`. O `git commit` (apenas) abre o ambiente vi de edição para que essas mensagens sejam editadas lá (verificar sub-sub-seção [Comandos para VI](#comandos-para-o-vi)).

❕ **Dica**: Para juntar (16) e (17) em uma única linha, utilizar o comando `git commit -a -m "[MSG]"` ou até `git commit -am "[MSG]"`.

Para verificar alterações no repositório local, segue os códigos:

```cmd
(19.1) λ git diff
(19.2) λ git diff --cached
(19.3) λ git diff --staged
```

O (18.1) mostra a diferença que ocorreu entre o meu repositório de trabalho e as alterações do último commit. No (18.2) e (18.3), as diferenças da área de preparação (*Staging Area*) são apresentadas. Caso goste de todas as alterações mostradas nessas diferenças, mandar para staged com o `git add`.

Já para listar o histórico de alterações, tem-se o comando:

```cmd
(20) λ git log
```

No (19), as modificações são listadas sempre da mais recente (topo) para mais antiga e cada uma carrega um número **SHA** (algoritmo que consegue gerar um número único) para fácil rastreio do commit e cada um carrega o Nome, Email, Data e Mensagem de Commit. Note-se também nesta etapa o conceito **HEAD**. **HEAD** é um ponteiro que aponta sempre para última modificação de uma branch. Há variações do `git log` que estão disponíveis no arquivo [CRIAR ARQUIVO COM TODOS OS COMANDOS] [Minhas Aliases](#minhas-aliases).

Para retornar a commits anteriores, usar o comando abaixo, sendo que não é necessário copiar o número SHA inteiro do commit, apenas os 5/6 primeiros dígitos já bastam.

```cmd
(21.1) λ git checkout [nºSHA]
(21.2) λ git checkout [nomeARQUIVO.txt]
(22.1) λ git reset --hard
```

Para retornar ao HEAD, utilizar o `git checkout [BRANCH]`. Há parâmetros que podem ser passados com o `checkout` como `-b`, que já cria e muda de branch de uma forma direta. No (20.2), é desfeito toda alteração do arquivo em questão e também, quando deletado algum, é possível recuperá-lo através deste programa. Mas note que se muitos arquivos forem modificados (excluídos), fica inviável refazer as alterações com este comando um po um. Assim, o (21.1) força o reset para o último commit. Se for apenas `git reset` é mostrado as opções de reset para escolha.

Caso opte por [retornar para um commit][5], há a opção de reset:

```cmd
(22.2) λ git reset --hard HEAD~1
(22.3) λ git reset --soft HEAD~1
(22.4) λ git reset --hard [nºSHA]
(23) λ git push origin HEAD --force
(24) λ git add .
(25) λ git commit -c ORIG_HEAD
```

A diferença entre a opção hard e soft é que se utilizar o hard, os commits posteriores ao do retorno serão perdidos, diferentemente do soft, que manterá todos. (21.2) e (21.3) apenas retornam um commit. Caso queira retornar mais, trocar o 1 para tanto de commits anteriores, ou faça a alteração pelo SHA RASH (21.4). Se o commit foi enviado para o repositório remoto, a opção (22) deve ser realizada. Assim, ao refazer as alterações, um novo `git add` deve ser feito e a mensagem de commit pode ser trocada com (24).

### 4.1. Clonando Repositórios

É possível não apenas clonar em uma URL remota, mas nos arquivos locais como:

```cmd
(26.1) λ git clone [OLD.DIRECTORY] [NEW.DIRECTORY]
```

Mas o mais utilizado é para clonar repositórios do GitHub:

```cmd
(27) λ cd [DIR]
(26.2) λ git clone [URL]
```

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 5. Comandos Intermediários e Avançados

Esta seção necessita necessariamente da configuração previamente realizada nas seções [1](#1-instalação-e-configuração), [2](#2-primeiros-passos) e [3](#3-comunicação-com-remotos-github-bitbucket-gitlab).

### 5.1. Enviando Branch para Remoto

Para enviar as alterações (commits) realizados localmente, é necessário "empurrar" com os comandos:

```cmd
(28.1) λ git push
(28.2) λ git push -u origin [BRANCH]
```

Caso não exista nenhum repositório remoto com o nome da branch indicada, será preciso enviar o comando `git push --set-upstream origin [BRANCH]`. Para simplificar, a opção `-u` substitui este comando (27.2).

### 5.2. Atualizando Branch Local com o Remoto

Em um cenário real, seriam duas pessoas trabalhando no mesmo repositório remoto, e consequentemente, com dois locais em diferentes estados. Caso o primeiro não tenha feito o `checkout` neste repositório, não será mostrado no comando `branch`. Mas mesmo que ele faça em alguma branch já criada pelo segundo, esta só ira aparecer no seu repositório local se tiver trazido o remoto pelo código:

```cmd
(29.1) λ git pull
(29.2) λ git fetch
```

Ainda assim, mesmo com o comando (28.1), se não for feito o checkout, não será mostrado as novas branchs no `git branch`. Para verificar quais são as novas, utilizar a opção dada em (8.4).

Como uma outra alternativa mais segura para o (28.1), há o (28.2), que baixa commits, arquivos e referências de um repositório remoto para seu repositório local, mas não obriga a realização de um merge das mudanças em seu repositório. O Git isola o conteúdo buscado do conteúdo local existente e não tem efeito algum no trabalho local de desenvolvimento. O conteúdo buscado tem de ser explicitamente verificado, usando o comando `git checkout`. Isso faz com que a busca seja uma forma segura de analisar commits antes de serem integrados ao repositório local. Portanto, se comparado com `git pull`, o *fetch* é a versão segura, irá baixar as atualização mas não as aplicará ao trabalho do repositório local, necessitando de um `git merge` para finalizar a atualização.

### 5.3. Deletando Branch do Remoto

Os comandos para remoção da branch local podem ser revisados em (8.5) e (8.6). No entanto, para remover uma beanch de um servidor, é necessário o seguinte comando:

```cmd
(30) λ git push --delete origin [BRANCH]
```

Tome muito cuidado com este comando caso trabalhe em grupo, pois pode ser que alguém esteja editando está branch e perderá o backup do servidor. **ATENÇÃO: ALINHE COM TODOS OS INTEGRANTES DO SEU TIME!**. Para confirmar que deu certo, abrir o GitHub e ver que a branch sumiu.

### 5.4. Renomeando uma Branch

O comando para renomear uma branch local, basta seguir as intruções abaixo:

```cmd
(31.1) λ git branch -m [nomeANTIGO] [nomeNOVO]
(31.2) λ git branch -m [nomeNOVO]
```

Adicionar a opção `-m` ao comando branch para realizar a mudança e em seguida, digitar o nome antigo da branch, seguido do novo, caso não esteja na branch de alteração, ou apenas o novo nome se estiver.

Não é possível renomear uma branch do servidor estando localmente. Para tal realização, há um caminho específico:

1. `git pull` - para trazer as últimas alterações do meu código remoto;
2. `git branch -m [nomeNOVO]` - para alterar o nome localmente;
3. `git push --delete origin [nomeANTIGO]` - apagar a antiga do servidor;
4. `git push -u origin [nomeNOVO]` - para mandar para servidor a branch com novo nome.

Mas **‼ ATENÇÃO:** para fazer este tipo de alteração, **ALINHE COM TODOS OS INTEGRANTES DO SEU TIME!**

### 5.5. Mesclando Alterações

Incorpora as alterações dos commits citados (desde o momento em que os seus históricos divergirem do ramo atual) para dentro do ramo atual. Este comando é utilizado pelo `git pull` para incorporar as alterações vindas de outro repositório e pode ser utilizado manualmente para mesclar as alterações de uma branch para outra.

```cmd
(32) λ git merge [BRANCH]
```

O Git merge traz as alterações já com um commit de `Merged`. Caso não queria este commit, basta utilizar a opção `--no-commit`. Uma observação importante é que o comando só realiza o commit se não existir conflitos, entretanto, se houver, é necessário tratá-los manualmente para a finalização do merge (ver subseção [5.6](#56-resolvendo-conflitos)).

Lembre-se que o merge carrega sempre o conceito de **TRAZER AS ALTERAÇÕES PARA A BRANCH ATUAL**.

### 5.6. Resolvendo Conflitos

Os conflitos acontecem quando em um mesmo arquivo, há alterações na mesma linha. Ou então quando algum desenvolvedor exclui arquivos enquanto outra pessoa faz alterações. Nesses casos, o Git não pode determinar qual está correto, sendo necessária uma resolução manual por parte do desenvolvedor que conduz o merge; o resto da equipe não fica ciente deles. O Git apenas marca os arquivos em conflito e interrompe o processo de merge.

Geralmente o Git apresenta um primeiro aviso, sempre forçando o developer a trazer as alterações do servidor:

```cmd
! [rejected]           main -> main (fetch first)
error: failed to push some refs to '[REMOTO]'
hint: updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Entretanto, ao tentar dar o `git pull`, é dada a mensagem de conflito:

```cmd
...
CONFLICT (content): Merge conflict in [ARQUIVO]
Automatic merge failed; fix conflicts and then commit the result.
```

Assim, basta abrir o editor de texto de sua preferência e decidir o que fazer com as mudanças e commit-as para fechar o commit (no final deve ter 2 commits na frente do servidor, um do merge e o outro da alteração).

❕ **DICA**: Sempre quando for começar uma alteração no código, SEMPRE realizar um `git pull`, para evitar conflitos deste tipo.

Há uma ferramenta gráfica que auxilia a resolução dos conflitos, chamada kdiff3 (vide [8.1] - software antigo - última release em 2014, mas leve e muito funcional).

### 5.7. Pull Request

O pull request, é o pedido para que o repositório original, ou uma branch do repositório original, faça a ação de pull (puxar) as atualizações do repositório fork ou de um branch do próprio repositório. Depois que uma pull request é aberta, você pode discutir e revisar as possíveis alterações com colaboradores e adicionar commits de acompanhamento antes que as alterações sofram merge no branch base.

Este pedido é realizado no servidor (GitHub, GitLab, BitBucket) e feito de uma maneira visual. No GitHub pode ser feito rascunhos de pull requests em repositório público.

### 5.8. Criando e Listando Tags

Como a maioria dos VCSs, o Git tem a capacidade de marcar pontos específicos no histórico de um repositório como sendo importantes. Normalmente, as pessoas usar essa funcionalidade para pontos de liberação de marca ( v1.0, v2.0e assim por diante).

```cmd
(33.1) λ git tag -a [NOME] -m "[MSG]"
(33.2) λ git tag -a [NOME] [nºSHA] -m "[MSG]"
(34.1) λ git tag
(34.2) λ git tag -l "[e.g. v1.2]"
(35) λ git show [NOME]
```

Para criar a sua Tag (da branch que estiver), utilizar o primeiro código alterando os campos [NOME] e [MSG]. Já o (33.2) é utilizado para quando você esqueceu de marcar uma Tag em algum commit e está fazendo isso posteriormente. O   (34.1) lista as tags em ordem alfabética; a ordem em que são exibidos não tem importância real. Para realizar uma busca mais filtrada (por padrões), utilizar a opção `-l` ou `--list` seguida do padrão requerido como em (34.2), que listará todas as Tags que apresentam o padrão v1.2 (e.g. v1.2.4-rc0). Caso queira ver os dados da tag junto com o commit que foi marcado, utilizar (35).

As Tags seguem o mesmo padrão de todos os outros elementos envolvendo Git para quando necessitar a utilização de uma, basta usar o comando `git checkout [NOMEtag]` para que seja feita a alteração para determinada Tag. Entretanto, uma mensagem é dada com algumas dicas:

```cmd
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again
```

Para excluir determinada Tag, seguir os procedimentos:

```cmd
(36) λ git tag -d [NOME]
(37) λ git push origin --delete [NOME]
```

No qual, (36) realiza a exclusão da Tag local, e (37) exclui a Tag do servidor remoto.

#### 5.8.1. *Semantic Versioning*

No mundo de gerenciamento de software existe algo terrível conhecido como inferno das dependências (“dependency hell”). Quanto mais o sistema cresce, e mais pacotes são adicionados a ele, maior será a possibilidade de, um dia, você encontrar-se neste poço de desespero.

Em sistemas com muitas dependências, lançar novos pacotes de versões pode se tornar rapidamente um pesadelo. Se as especificações das dependências são muito amarradas você corre o risco de um bloqueio de versão (A falta de capacidade de atualizar um pacote sem ter de liberar novas versões de cada pacote dependente). Se as dependências são vagamente especificadas, você irá inevitavelmente ser mordido pela ‘promiscuidade da versão’ (assumindo compatibilidade com futuras versões mais do que é razoável). O inferno das dependências é onde você está quando um bloqueio de versão e/ou promiscuidade de versão te impede de seguir em frente com seu projeto de maneira fácil e segura.

Como uma solução para este problema proponho um conjunto simples de regras e requisitos que ditam como os números das versões são atribuídos e incrementados.

É isso que o **SemVer** faz, regula e traz todas as interpretações para um ponto comum. O Semver faz a seguinte interpretação:

```cmd
major.minor.patch
```

Onde:

- **Major**: quando fizer mudanças incompatíveis na API;
- **Minor**: quando adicionar funcionalidades mantendo compatibilidade;
- **Patch**: ou Correção, quando corrigir falhas mantendo compatibilidade

**Rótulos adicionais** para *pre-release*, rc (*release candidate*) e *build* estão disponíveis como extensão, ficando da seguinte maneira:

- Pré-release: 0.0.1-alpha, 2.0.0-beta, 2.0.0-rc1
- Build: 1.0.3+12345, onde 12345 é o número da build
- Ambos: 2.0.1-alpha+12344

O rótulo de *pre-release* é importante para informar ao consumidor de seu pacote que ele ainda é um trabalho em progresso – *work in progress* – portanto ainda é uma versão instável e está sob constante modificação.

Existem algumas convenções ou princípios sobre isso. Por exemplo, se seu pacote estiver marcado como um *rc – release candidate*, ou seja, um candidato a ser um produto final – não mais irá sofrer grandes alterações, apenas correções, até que esteja maduro suficiente para ser lançado como uma versão final.

Já, deixar explícito o número da *build* é interessante, talvez, apenas em tempo de *build n’release*, pois é comum uma mesma versão de *Patch* ter várias tentativas de *release* até sua publicação.

### 5.9. Stash

O comando `git stash` arquiva (ou faz o *stash*) de alterações que você fez na cópia de trabalho durante um determinado período, para que você possa trabalhar em outra coisa, depois voltar e fazer a reaplicação mais tarde. O *stashing* é útil quando você precisa alternar com rapidez o contexto e trabalhar em outra coisa, mas está no meio da alteração de código e não está pronto para fazer commit.

Para fácil entendimento, imagine o seguinte ambiente: **dev1** está desenvolvendo na *branch B* do projeto e já realizou diversas modificações. o **dev2** pede pra que ele confira uma configuração feita na *branch B*. Ao tentar alterar de *branch* (20), é dado o seguinte erro:

```error
error: Your local changes to the following files would be overwritten by checkout:
        index.html
Please commit your changes or stash them before you switch branches.
Aborting
```

Para isso, commitar as mudanças ou revertê-las (21.1) funcionaria. Entretanto, não quero nenhuma das opções. Assim, utilizar stash para criar uma pilha com essas, reverter, mudar de branch e logo quando voltar para a mesma, puxar do stash aquelas mudanças.

```cmd
(38.1) λ git stash
(38.2) λ git stash list
(38.3) λ git stash save "[MSG]"
(38.4) λ git stash apply
(38.5) λ git stash pop
(38.6) λ git stash drop
(38.7) λ git stash show
(38.8) λ git stash clear
```

Para salvar o stash com um nome desejado, utilizar (38.3). Para aplicar a o primeiro estado que está no topo da pilha (mais recente), aplicar utilizando (38.4) ou (38.5). A diferença entre os dois é que o primeiro, mantém o stash do topo na pilha (sendo necessária posterior exclusão com (38.6)), já o segundo, remove-o assim que dado o comando. Tanto para (38.4), (38.5) e (38.6) é possível realizar os comandos para stash que estão abaixo do topo da pilha, acrescentando o nome do stash, como `stash@{3}`.

Para visualizar comparações de stash, utilizar (38.7). Acrescentando a opção `-p` ou `--patch` tem-se as alterações completas realizadas naquele stash. Use (38.8) para excluir todos os itens da pilha.

### 5.10. CherryPick

O `cherry pick` é um comando poderoso do Git que permite ao usuário selecionar commits específicos para trazer ao branch desejado. Antes de dar o comando, certifique-se de que está na branch que queira trazer o commit.

```cmd
(39.1) λ git cherry-pick [nºSHA]
(39.2) λ git cherry-pick [A]^..[B]
(39.3) λ git cherry-pick [A]..[B]
```

Apesar de ser um comando simples e muito bom de ser utilizado, não é recomendada sua utilização pelas boas práticas do Git, cuidado para não sair duplicando commits na sua linha do tempo, use com moderação. Sempre opte por utilizar os recursos do **Git-flow**, como criar um **Hot-fix** para seu problema. Veremos com mais detalhes nas seções futuras.

Para copiar um intervalo de commits, usar a sintaxe (39.2) para copiar inclusive o `[A]` ou (39.3) para ignorar o `[A]`.

### 5.11. Rebase

Rebase é um dos dois utilitários do Git que se especializam em integrar alterações da ramificação para outra. O outro utilitário de integração de alterações é o `git merge`. A mesclagem (merge) é uma alteração de registro de avanço. Como outra opção, o rebase tem recursos poderosos para reescrever o histórico. O rebase tem 2 modos principais: os modos "manual" e "interativo". Será tratado os diferentes modos de rebase com mais informações ainda nessa seção, apresentando uma aplicação real *step-by-step*.

Tendo o cenário a seguir, da *branch* **master** com 3 commits (A, B e C):

```cmd
A<---B<---C
          |
          |
       |Master|
          |
         HEAD
```

Após fazer o commit C, é criado uma nova *branch* com o nome **design** a partir da master:

```cmd
        HEAD
          |
       |design|
          |
          |
A<---B<---C
          |
          |
       |Master|
```

Realizado um novo commit (D) no *branch* **design**:

```cmd
                  HEAD
                    |
                |design|
                    |
                    |
                .---D
               /
A<---B<---C<--´
          |
          |
       |Master|
```

Ao retornar para a *branch* **master**, tem-se o HEAD na seguinte posição

```cmd
                |design|
                    |
                    |
                .---D
               /
A<---B<---C<--´
          |
          |
       |Master|
          |
         HEAD
```

Um novo commit (E) é realizado na **master**, apresentando a seguinte bifurcação:

```cmd
                |design|
                    |
                    |
                .---D
               /
A<---B<---C<--´-----E
                    |
                    |
                |Master|
                    |
                   HEAD
```

Nessa hora, o rebase da **master** na **design** é feito com os comandos: `git checkout design` && `git rebase master`

```cmd
                |design|
                    |
                    |
                .---D<----E
               /          |
A<---B<---C<--´           |
                       |Master|
```

Com o rebase, os commits a mais da master (E) vão para o topo da branch **design**.

Assim, ao final do exemplo de rebase, os commits ficaram:

**master:** A, B, C, D, E <br>
**design:** A, B, C, D

O rebase é muito utilizado para quando você quiser ter um cenário linear do seu projeto, trazendo tudo das *branchs* para um só uma. Mas há alguns pontos que necessitam destaque: segurança e rastreabilidade. O problema é que o rebase altera o histórico, assim como outros comandos do git (como os que levam o atributo --hard). Por isto ele é recomendado apenas em casos bem específicos. O Git não tem a premissa de proteger a qualquer custo o histórico de alterações mas de, por padrão, preservar isto.

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 6. Mensagens de Erro, Workarounds e Dicas

### 6.1. Alterações Não Versionadas

A mensagem de erro abaixa é dada sempre quando o usuário quer trocar de uma branch para a outra, mas tem alterações em arquivos da branch atual que mão foram "commitadas".

```error
error: Your local changes to the following files would be overwritten by checkout:
  index.html
Please commit your changes or stash them before you switch branches.
```

Para resolvê-lo, realizar algum dos passos a seguir:

1. Commitar as mudanças na branch atual;
2. Colocar as mudanças em stash utilizando o `git stash`
3. Excluir as modificações com `git reset --hard`

### 6.2. Desfazendo Commits

Quando realizar algum commit errado e quiser alterar mensagem, arquivos e qualquer alteração realizada naquele commit, seguir os passos a seguir:

1. `git commit -m "Something terribly misguided"`
2. `git reset HEAD~`
3. Editar os arquivos necessários
4. `git add .`
5. `git commit -c ORIG_HEAD`

O comando em (2) é responsável por refazer um commit. Isso irá desfazer seu último commit enquanto deixa sua *branch* de trabalho (o estado de seus arquivos no disco) intocada. É preciso adicioná-los novamente antes de confirmá-los. Caso queira retornar para outro commit em específico, colocar na frente do `HEAD~` o valor de commits que devem ser retornados.

No item (5) é confirmado as alterações, reutilizando a mensagem de confirmação antiga. `reset` copia o antigo cabeçalho para `.git/ORIG_HEAD`; O commit com `-c ORIG_HEAD` irá abrir um editor, que inicialmente contém a mensagem de log do commit antigo e permite que você o edite. Se não precisar editar a mensagem, pode usar a opção `-C`.

**Alternativamente, para editar o commit anterior (ou apenas sua mensagem)**, `git commit --amend` irá adicionar mudanças dentro do índice atual ao commit anterior, podendo adicionar a opção `-m [MSG]`, para não editar pelo VIM. Ocorre quando você acabou de alterar alguma coisa e adicioná-la na *staging*, entretanto, esta alteração deveria estar em um commit anteriormente feito por você e que não foi enviado para o servidor.

**Para remover (não reverter) um commit que foi enviado para o servidor**, é necessário reescrever o histórico com `git push origin master --force`.

Estes dois POSTs no StackOverflow aborda maneiras diferentes de realizar o Undo & Redo de um commit: [How do I undo the most recent local commits in Git?][12] e [How can I move HEAD back to a previous location? (Detached head) & Undo commits][13].

O segundo link mostra o `git reflog`, que você pode usar para determinar o SHA-1 para o commit ao qual deseja reverter. Depois de obter esse valor, use a sequência de comandos conforme explicado acima.

### 6.3. Padronizando Commits

Para maiores informações envolvendo a padronização de commits, acesse a documentação [Padronização de commits - Jonathan T. Silva][16].

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 7. Utilidades

### 7.1. GitFlow

É um fluxo de trabalho para o Git criado para facilitar o processo de desenvolvimento com uma série de comandos novos. O nome por trás desse modelo é *Vincent Driessen* que, em 2010, escreveu em seu blog pessoal a maneira que ele pensou ser a mais simples de se trabalhar com o Git em larga escala.

Mesmo sendo um método que auxilia o nosso trabalho devemos ter algumas ressalvas diante de como é aplicado: se usado de maneira inadequada, o Git Flow pode se tornar bastante ineficiente e gerar uma experiência não muito agradável.

Além disso, existe um repositório no GitHub onde podemos ver o código aberto do modelo criado. O código em si é feito todo em Shell e o commit mais recente foi de 2012.

![GitFlow][git-flow]

Basicamente, a estruturação se define em:

**feature**: Todos os recursos / novas funções / principais refatorações são feitas em branches de recursos, que se ramificam e são mesclados de volta ao branch **develop** (geralmente após algum tipo de revisão por pares).

**release**: Quando recursos suficientes se acumulam ou o próximo período de lançamento se aproxima, um novo ramo de lançamento é ramificado de desenvolvimento, que é exclusivamente dedicado a testes / correção de bugs e qualquer limpeza necessária (por exemplo, alterar alguns nomes de caminho, diferentes valores padrão para instrumentação, etc.).

**hotfix**: Se um grande problema for encontrado após o lançamento, a correção é desenvolvida em uma ramificação de hotfix, que é ramificada do master. Esses são os únicos ramos que irão se ramificar do master.

**Nota**: Qualquer confirmação no master é uma confirmação de mesclagem (de uma versão ou branch de hotfix) e representa uma nova versão enviada ao cliente.

Esteja ciente de que este modelo se destina principalmente a:

1. grandes projetos de software que seguem;
2. versão de lançamento clássico, e;
3. têm uma equipe de QA separada. Muitos repositórios populares no GitHub seguem um modelo mais simples.

### 7.2. Alias

O Git não infere automaticamente o seu comando se você digitá-lo parcialmente. Se você não quiser digitar todo o texto de cada um dos comandos do Git, pode facilmente configurar um alias para cada comando usando git config. Aqui estão alguns exemplos que você pode querer configurar:

(40.1) λ git config --global alias.co checkout
(40.2) λ git config --global alias.br branch
(40.3) λ git config --global alias.ci commit
(40.4) λ git config --global alias.st status

Isso significa que, por exemplo, em vez de digitar `git commit`, você só precisa digitar `git ci`. Conforme você usa o Git, provavelmente também usará outros comandos com frequência; não hesite em criar novos apelidos.

Entretanto, há uma outra forma mais fácil e visualmente mais intuitiva de criar suas aliases para o Git, basta adicioná-las no código `.bashrc` citado na subseção [3.2](#32-cruzando-chave-ssh):

```bash
# Aliases
alias ci='git commit'
```

#### 7.2.1. Minhas Aliases

Na tabela abaixo, estão apresentadas as aliases criadas pelo autor:

| Alias |     Git Command     |                                                    Description                                                    |
| ----- | :-----------------: | :---------------------------------------------------------------------------------------------------------------: |
| gs    | `git status` | Verificar status do Git |
| gch   | `git checkout --` |  |
| gl    | `git log` |  |
| glo   | `git log --oneline` |  |
| glp   | `git log --pretty=format:[FORMATO]` | "%C(yellow)%h %Cred%ad %Cblue%an%Cgreen%d %Creset%s" --date=short' #"%h%x09%an%x09%ad%x09%s" ---> %h = abbreviated commit hash ; %x09 = tab (character for code 9) ; %an = author name ; %ad = author date (format respects --date= option) ; %s = subject  |
| gfp   | `git fetch --prune` | Para ter certeza se está tudo ok, combinado remoto com local, se não, deleta no local o que não estiver no github |
| gps   | `git push` |  |
| gpl   | `git pull` |  |
| gplp  | `git pull --allow-unrelated-histories` | Para quando acontecer de de travar o push 'non-fast-forward' |
| gffs  | `git flow feature start` |  |
| gfff  | `git flow feature finish` |  |
| gffp  | `git flow feature publish` |  |

### 7.3. Grep

O comando grep atua como um filtro para as pesquisas de branchs e tags do meu projeto. Procura padrões especificados nos arquivos rastreados na árvore de trabalho, *blobs* registrados no arquivo de índice ou *blobs* em determinados objetos de árvore.

Exemplo da utilização de `grep`:

```cmd
(41.1) λ git branch | grep R1
> R1-TASK1
> R1-TASK2
> R1-TASK3
```

```cmd
(41.2) λ git tag | grep 1
> v1
> v1.2
> v1.4.1
```

<!-- Back to Top -->
<a href="#meu-cheatsheet-de-git"><img width="40px" src="https://icons.veryicon.com/png/o/internet--web/property-2/back-to-top-1.png" align="right" /></a>

## 8. Ferramentas Gráficas 

Nesta seção veremos as ferramentas gráficas mais famosas para apoio na utilização do Git (exceto extensões e editores).

### 8.1. [kdiff3][11]

Ao realizar a instalação padrão do software, ir para o Git Bash e inicializar:

```cmd
(31.1) λ git config --global --add merge.tool kdiff3
(31.2) λ git config --global --add mergetool.kdiff3.path "[DIR]"
(31.3) λ git config --global --add mergetool.kdiff3.trustExitCode false
(32) λ git mergetool
```

O arquivo .gitconfig será editado com os comandos. Para listar os comandos atuais do arquivo, basta adicionar a opção list: `git config --global --list`. Com o código (31.1) é passado para o arquivo qual a ferramenta externa de merge será utilizada. O (31.2) configura o local que o software kdiff3 foi instalado, geralmente: "C:/Program Files/KDiff3/kdiff3.exe". Por fim, quando tiver um ambiente em conflito, utilizar (32) para que seja resolvido pelo kdiff3.

![kdiff3][kdiff3]

#### 8.2. [Sourcetree][14]

Sourcetree simplifica como você interage com seus repositórios Git para que você possa se concentrar na codificação. Visualize e gerencie seus repositórios por meio da GUI Git simples do Sourcetree. É da Atlassian, portanto, integração total com Jira, Confluence, BitBucket, entre outros.

- Simples para iniciantes: diga adeus à linha de comando - simplifique o controle de versão distribuída com um cliente Git e deixe todos atualizados rapidamente.
- Poderoso para especialistas: perfeito para tornar os usuários avançados ainda mais produtivos. Revise changesets, stash, escolha a dedo entre branches e muito mais.
- Visualize seu código: ver realmente é acreditar. Obtenha informações sobre qualquer filial ou submeta com um único clique.
- Git e Hg em seu desktop: uma GUI com todos os recursos que oferece um processo de desenvolvimento eficiente e consistente pronto para uso. Funciona com Git e Mercurial.

![sourcetree][sourcetree]

#### 8.3. [GitKraken][15]

GitKraken é uma nova interface gráfica para git. Eu sou um grande fã do git na linha de comando e, mesmo que eu tenha usado diferentes GUIs no passado, eu sempre volto para o console.

A propósito, GitKraken parece promissor graças a um conjunto de características interessantes. Vamos dar uma olhada nas quais que mais me impressionaram depois de uma primeira usada.

Esta é provavelmente a melhor característica no momento, uma visão gráfica muito bem feita da sua rede git que lhe permite entender qual é o status atual do seu repositório em termos de commits e branches. Cada ponto no gráfico representa um commit e é interativo. Ao selecionar um deles, você pode ver todas as mudanças aplicadas desse commit, quem fez o push, a descrição do commit e, mais importante, se você clicar no botão direito sobre ele você pode executar imediatamente uma série de ações que não são tão triviais na linha de comando:

- cherry-pick;
- criar um branch a partir de um commit específico;
- criar uma nova tag apontando para aquele commit;
- reset master para aquele commit;
- editar a mensagem do commit.

![gitkraken][gitkraken]

<!-- Markdown's Links -->
<!-- SITES -->
[1]: https://git-scm.com/
[2]: https://git-scm.com/download/linux
[3]: https://cmder.net/
[4]: https://www.cs.colostate.edu/helpdocs/vi.html
[5]: https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git
[6]: https://www.notion.so/jonathansmar/Comunicar-Git-e-BitBucket-d528f973813047a7a8db45d0dccf570b#7e19b5d9b12f4c5ab6055de146ceff9e
[7]: https://rdmd.readme.io/docs/code-blocks
[8]: https://www.microsoft.com/pt-br/p/windows-terminal/9n0dx20hk701#activetab=pivot:overviewtab
[9]: https://www.alura.com.br/artigos/visualstudio-code-instalacao-teclas-de-atalho-plugins-e-integracoes
[10]: https://git-school.github.io/visualizing-git/#free-remote
[11]: http://kdiff3.sourceforge.net/
[12]: https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git
[13]: https://stackoverflow.com/questions/34519665/how-can-i-move-head-back-to-a-previous-location-detached-head-undo-commits/34519716#34519716
[14]: https://www.sourcetreeapp.com/
[15]: https://www.gitkraken.com/
[16]: https://github.com/JonathanTSilva/TP-Standardization/blob/main/Articles/Padroniza%C3%A7%C3%A3o%20de%20commits.md

<!-- ARQUIVOS -->

<!-- IMAGENS -->
[git-school]: https://kancane.nl/images/git-remote-6.png
[kdiff3]: https://cdn.kde.org/screenshots/kdiff3/diffscreen_two_way.png
[git-flow]: https://user-images.githubusercontent.com/58694273/135694279-55ae02a5-917a-4822-9c96-57f652f1dc17.png
[sourcetree]: https://wac-cdn.atlassian.com/dam/jcr:580c367b-c240-453d-aa18-c7ced44324f9/hero-mac-screenshot.png?cdnVersion=1830
[gitkraken]: https://1v5ymx3zt3y73fq5gy23rtnc-wpengine.netdna-ssl.com/wp-content/uploads/2021/03/gk-product-2.png

<!-- COMENTÁRIOS -->
