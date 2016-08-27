# Lista de comandos GIT

## Git Bash
#### Abrir Git Bash
```sh
Acessar diretório de trabalho, clicar com botão direito do mouse no menu de contexto selecionar Git Bash.
```
![alt dica](https://dl.dropboxusercontent.com/u/13529137/Imagens/abrir-git-bash.jpg "menu de contexto")

#### Configurações básicas e globais
```sh
$ git config --global user.name "[seu nome]"
$ git config --global user.email [seu e-mail]
$ git config --global color.vi true
```

#### Verificar configurações (qualquer tempo)
```sh
$ git config --list
    ou
$ git config user.name
```

## Ajuda
```sh
$ git help config
    ou 
$ git [verbo] --help
```

#### Criar repositório
```sh
$ mkdir [nome-dirretorio]
$ cd pasta
$ git init
```

#### Criar arquivo
```sh
$ touch [nome-do-arqiovo]
```

#### Abrir arquivo
```sh
$ vim [nome-do-arqiovo]
```
#### comandos do vim
Salvar: **Digite Ctrl + C** em seguida precione **precione :** [e escolha a segir]
1. **Q** sair do vim
2. **Q!** sair sem salvar
3. **WQ** salvar e sair
4. **QA** sair de todas as edições em uso

#### Adicionar arquivo(s) ao próximo commit
```sh
$ git add [arquivo1] [arquivo2] ...
    ou
$ git add .
```

#### Commit (em 3 estágios)
```sh
$ git commit -m "[mensagem]"
```
1. **Working Diretory** (untracked Files) 
    `$ git add [nome-do-arquivo]`
2. **Staging Area** (changes to be committed) 
    `$ git commit -m "mensagem"`
3. **Diretory** (repositório) 
    `Está sendo controlado pelo vercionador`

## Fluxo de Verções
##### Retirando Arquivos (do Staging Area)
`$ git reset HEAD [nome-do-arquivo]`
Volta alguns ou todos oa arquivos.


##### Voltando Verções
`$ git checkout [nome do hash]` 
Voltará para o hash especificado. Ele exclue
> O comando anterior coloca os arquivos em um **branch indefinido**

> `$ git branch` (mostra o branch atual)

> `$ branch checkout master` (volta para obranch master)

`$ git reset HEAD~1 --soft` (simplesmente volta 1 commit)

`$ git reset HEAD~1 --HEAD` (volta 1 commit, **CUIDADO**, ele tambem exclui os arquivos)

##### Voltando ao Estado Original do Arquivo
`$ git checkoutn [nome-do-arquivo.xpto]` (ele volta ao estado original do arquivo, removendo as alterações do arquivo)

=====================================================================


#### Dicas
`$ git add .` Adiciona todos os arquivos

`$ git add *.php` [ou qualquer extenção]

`$ git commit -a -m "mensagem"` commit direto, pulando etapas.

`$ git commit` [sem parámetros], abrirá o editor padrão para digitar a mensagem.

===============================================================================

# Log
```sh
$ git log (traz todos)
$ git log -p (mostra as alterações nos arquivos enviados commit)
$ git log -p 2 (mesmo anterior, com apenas 2 registros)

$ git log ---stat (mostra as estatísticas de alterações)

$ git log --pretty = online (traz 1 por linha)

$ git log --pretty = format: "%h - %an, %ar : % s" (NOME, DATA, DESCRIÇÃO)

$ git --since = 2.days [2.weeks]...

    dica
Ctrl + C [sair do log]
```

=================================================================================

## Ignorando Arquivos
`$ vim .gitignore` cria o arquivo e abre o editor.
> Cloque a lista de nomes de arquivos, linha a linha.

> Se for nome de diretório, coloque o nome e "/" no final.

=================================================================================

# Branch
##### Criar
```sh
$ git checkout -b [branch]
```
##### Excluir
```sh
$ git branch -d [branch]
```
##### Ver o branch atual
```sh
$ git branch
```
##### Trocar de Branch
```sh
$ git checkout [branch]
```
##### Merge
```sh
$ git checkout master (entrar no branch)
$ git merge [nome-do-branch]
```

==============================================================================

## GITHUB
##### Criando chave de autenticação

1. ***Gerar*** a chave:
`$ ssh-keygen`

2. Para ***visualizar*** a chave criada, digite no terminal:
`$ ~/.ssh/`

3. ***Listar***: `$ ls`
github_rsa  github_rsa.pub  id_rsa  id_rsa.pub  known_hosts

4. pegar o ***codigo***: `$ cat id_rsa.pub`

5. ***NO GIT***, vá em settings/SSH and GPG keys, botão New SSH key. Dê um titulo descritivo para chave e cole o codigo no campo correspondente.


##### Criando primeiro repositório
***Dica:*** Crie um repositório totalmente ***limpo*** (não marque a opção: Initialize this repository with a README), sem nenhum arquivo, assim ele será criado sem nenhum Branch, deste modo no seu primeiro ***Push*** ele vai criar toda estrutura, caso contrario você terá que ***clonar*** o repositório.

***Proximo passo, o propio git ajuda:***
##### Fazendo o primeiro push
````sh
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git remote add origin git@github.com:jadirbento/teste.git
$ git push -u origin master `
````

##### Push em outro branch
O push acontece no branch atual, onde você está. Para subir um outro branch você precisa primeiro trocar de branch local.

````sh
$ git branch ->lista todos
$ git checkout nomedobranch
$ git push origin master nomedobranch (qualquer nome)
````

##### Clonando...
1. entre no repositório e clique no botão "Clone or download".
2. copie a url.
3. no terminal `$ git clone git@github.com:jadirbento/git-help.git (cole a url)`.
4. ***Dica*** se você der um espaço, deois da url, poderá dar um outro nome para o clone.
***Caso tenha outros branch e você quer clonar tambem***
`$ git branch -a ` -> ele vai listar os locais e os remotos.
5. Criar `$ git checkout -b meubranch origin/meubranch` ->ele cria local com base no remoto.

##### Pegar atualizações (PULL) no repositório remoto
Explo: quando o seu colega fala, acabei de fazer um push, pega aí as alterações.
`$ git pull origin master`

##### Sincronizar tudo no repositorio remoto
`$ git pull` ->cria todos os branch remotos no seu local.

##### Push com o novo branch
`$ git push origin npme-do-novo-branch`














