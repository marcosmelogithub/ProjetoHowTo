# GitHub Quick Guide
---
### 1. Comandos Git

**1.1.** Iniciar o controle de versionamento do git
>**Comando:**
>``` git init ```
>> **a)** Para executar o comando acima é preciso estar na pasta local do repositório
>> **b)** Esse comando irá criar uma subpasta oculta com o nome de *.git*, onde será realizado todo o controle de versionamento do projeto pelo git
>> **c)** Esse é o comando que é necessário ser executado uma única vez quando um novo repositório for criado

**1.2.** Adicionar um arquivo na lista de commit (stage)
>**Comando**
>```git add [nome-do-arquivo]```
>> **a)** Para que um arquivo que foi alterado seja "*commitado*", é necessário adicioná-lo à fila de *stage*, pois somente os arquivos que estiverem no *stage* é que poderão ser "*commitados*"

**1.3.** Remover um arquivo da lista de commit (stage)
>**Comando**
>```git restore --staged [nomearquivo]```
>> **a)** Essa ação irá retirar um arquivo da lista de *commit*, caso se entenda que são necessárias mais alterações antes do *commit*

**1.4.** Verificar quais os arquivos estão no *stage* para serem "*commitados*"
>**Comando**
>```git status```

**1.5.** "*Commitar*" arquivos
>**Comando**
>```git commit -m ["comentário"] [.|nome-do-arquivo]```
>> **a)** O commit é a ação de *aceitar* as alterações realizadas nos arquivos, tornando a versão alterada como a atual
>> **b)** É sempre aconselhável informar um comentário para que quando se fizer a leitura dos *commits* no github será mais fácil entender de se trata o commit
>> **c)** Pode-se fazer o *commit* arquivo por arquivo, nesse caso informa-se o nome do arquivo, ou fazer de todos os arquivos que estão no *stage* usando o "." no lugar do nome do arquivo
>>**d)** O ponto de atenção é que o comentário será o mesmo para todos os arquivos, sendo o comentário para todo *commit*. Caso queira especificar a alteração de cada arquivo, faça o *commit* individualmente por arquivo

**1.6.** Associar com o branch no github
>**Comando**
>```git branch -M main```
>> **a)** Esse comando informará ao controle do git local a qual branch no github será realizado a associação para a execução do comando *push*
>> **b)** Por default, quando um novo repositório é criado no github é associado automaticamente à branch main. Portanto, esse comando é necessário somente antes do primeiro *push*, sendo que nas manutenções futuras do repositório esse comando não é necessário

**1.7.** Sincronizar os *commits* do repositório local com o github
>**Comando I**
>```git remote add origin https://github.com/[githubuser]/[nomerepositório].git```
>> **a)** A ação é sincronizar o git local com o git remoto para que ele entenda que será realizado um *push*
>> **b)** Esse comando especificamente é utilizado quando se cria um novo repositório, iniciando o git local pela primeira vez, tem que informar ao comando a url *https://github.com/[githubuser]/[nomerepositório].git*, substituindo:
>>> ***githubuser*** pelo nome da conta no github
>>> ***nomerepositório*** pelo nome do repositório criado no github
>>>
>**Comando II**
>```git remote add origin main```
>> **a)** Se já é um repositório existente e está em manutenção, não é necessário informar a url, substituindo pelo nome da branch que, por default, é *main*

**1.8.** Enviar os *commits* local para o github
>**Comando**
>```git push -u origin main```
>> **a)** Esse comando irá enviar todos os arquivos "*commitados*" para o github, gerando uma nova versão do projeto no github

**1.9.** Listar os *commits* enviados ao github
>**Comando**
>```git log --pretty=format:"%h - %ad : %s" [nome-arquivo]```
>> **a)** Essa ação listará todos os *commits* que foram enviados ao github
>> **b)** Se informar o nome do arquivo, listará todos os commits que envolveram aquele arquivo
>> **c)** Se não informar o nome do arquivo, serão listados todos os *commits* independentemente de arquivos
>> **d)** Essa ação é auxiliar quando se quer restaurar um *commit* para retornar à posição anterior qualquer
>>> **Um exemplo de como a lista virá**
>>>>70680f1 - Sun Feb 22 20:17:20 2026 -0300 : 1a alteração no repositório
>>>>207bf39 - Sun Feb 22 19:45:41 2026 -0300 : README.md criado
>>>>sendo, 70680f1 e 207bf39 as hashes dos commits, que é um id único por *commit* e é utilizado para indicar qual *commit* se deseja restaurar
>>>>no final de cada linha tem o comentário informado quando o commit foi realizado
>>>>e entre o hash e o comentário, são as informações de quando o *commit* foi realizado

**1.10.** Clonar um repositório do github para o repositório local
>**comando**
>```git clone https://github.com/[githubuser]/[nomerepositório].git```
>> **a)** Essa ação irá "trazer" para a máquina local o último *commit* completo
>> **b)** É normalmente executado quando se tem um repositóriono github e é preciso dar manutenção nos arquivos desse repositório, então é preciso primeiro trazer o repositório para uma pasta local (repositório local) para se trabalhar nos arquivos e no final das manutenções realizar o *push* para o github gerando mais um *commit* atualizado no github
>> **c)** Por default o comando cria uma pasta local com o mesmo nome do repositório, mas se quiser um nome de pasta local diferente basta adicionar no final do comando o nome da pasta local
>> **d)** substituir [githubuser] pelo nome da conta no github
>> **e)** substituir [nomerepositório] pelo nome do repositório que se deseja clonar

**1.11** Restaurar arquivo de um *commit* do github
>**Comando I**
>```git restore [nome-do-arquivo]```
>> **a)** Irá restaurar um arquivo do último *commit* no github e substituirá, se existir, o arquivo na pasta local
>> **b)** É usado quando se quer retornar um arquivo especifico da pasta local que está em manutenção à posição do último *commit* enviado ao github
>>
>**Comando II**
>```git restore --source=[hash] [arquivo-restaurar]```
>> **a)** Irá restaurar um arquivo de um *commit* informado no [hash]
>> **b)** Irá retornar o arquivo do *commit* informado, não importando quantos *commits* para trás, e substituirá o arquivo na pasta local onde se está realizando manutenção
>>
>**Comando III**
>```git restore .```
>> **a)** Irá restaurar integralmente o último *commit* enviado ao github
>> **b)** Essa ação pode se confundir com o *clone*, mas tem uma diferença sutil:
>>> vamos imaginar que durante a manutenção do repositório local foi criado um novo arquivo e e alterado outros, mas notou que as alterações nos arquivos que vieram com o *clone* não deviam ter sido alterados, mas o novo arquivo deve ser mantido, então o *git restore .* irá trazer todos os arquivos do último *commit* enviado ao github e ainda manter os arquivos criados e assim que um novo *push* for realizado terá um novo *commit* atualizado, inclusive com os novos arquivos
>>> se usar o *git clone*, toda a pasta local será substituída e os novos arquivos serão perdidos, pois a pasta local se tornará idêntica ao último *commit* enviado ao github

**1.12** Listar branches
>**Comando**
>```git branch```
>> **a)** Listará todas as branches do repositório
>> **b)** A branch ativa terá um "*" antes do nome da branch

**1.13** Alternar entre as branches existentes
>**Comando**
>```git checkout [nome-da-branch]

**1.14** Criar uma nova branch a partir da branch ativa
>**Comando**
> git checkout -b [nome-da-nova-branch]
>> **a)** Uma nova branch será criada com o mesmo conteúdo da branch ativa
>> **b)** Uma prática para nomear uma branch é:
>>> - inserir feature/ ou bug/ e logo depois da barra o nome da branch
>>> - feature/ para implementações, alterações ou evoluções
>>> - bug/ para correção de bugs

**1.15** Fazer o push da nova branch para o github 
>**Comando**
>```git push --set-upstream origin [nome-da-nova-branch]```
>> **a)** Após esse comando o github terá duas branchs, a main, que é a branch quando o repositório foi criado e a nova branch criada
>> **b)** Esse comando, com o parâmetro *--set-upstream*, só é necessário quando se cria uma nova branch
>> **c)** Se fizer novas alterações na branch, basta dar o comando *git push origin [nome-da-branch]

**1.16** Deletar um branch
>**Comando**
>```git branch -d [nome-da-branch]```
>> **a)** Para deletar um branch, ela não pode ser a branch ativa, ou seja, quando listar as branches, ele não pode estar com um asterico antes do nome

**1.17** Atualizar a branch local com a branch do github
>**Comando**
>```git pull```
>> **a)** Esse comando é dado estando na branch selecionada.
>> **b)** Irá sincronizar a branch local com a branch do github


**1.15** ***MUITO IMPORTANTE*** entender sobre branches
> **i)** Como boa prática não se trabalha diretamente na branch ***main***, que é a branch principal, criada quando o repositório foi criado e normalmente é a branch de produção.
> **ii)** Quando se fizer o push não corre o risco de alterar a branch ***main*** com algo que possa estar errado ou indevido, aumentando assim a proteção da ***main***.
> **iii)** Criando uma branch nova, a partir da ***main*** para se trabalhar, pode-se ter um time com vários desenvolvedores, cada um na sua branch, e ninguém interfere na branch do outro e nem corre o risco de criar algum problema na branch ***main***.
> **iv)** Posteriormente, o lider ou responsável pelo projeto, irá fazer um merge de todas as branches que foram *"pushed"* no github para a branch ***main*** e fazer o *deployment* em produção da nova versão.
> **v)** Após fazer o merge da branch de desenvolvimento com a main, pode-se excluir a branch no github ou mesmo deixá-la para efeito de histórico, vai depender das diretrizes da gestão do projeto.


---
### 2. Sequência lógica para um novo repositório

**2.1.** Criar um novo repositório no github
**2.2.** Criar uma pasta local (de preferência com o mesmo nome do repositório criado)
**2.3.** "Entrar" na pasta local criada
**2.4.** Executar o item 1.1.
**2.5.** Criar o arquivo README.md
>**Comando**
>```touch README.md```

**2.6.** Executar o item 1.2.
**2.7.** Executar o item 1.5.
**2.8.** Executar o item 1.6.
**2.9.** Executar o item 1.7., Comando I
**2.10.** Executar o item 1.8.
> O repositório local está "*commitado*" no github

---
### 3. Sequência lógica para um repositório existente no github

**3.1.** Executar o item 1.10
> **a)** É bastante recomendado que antes que inicie as manutenções em um repositório, faça um clone do último *commit* para garantir que está partindo de uma posição atualizada
> **b)** Se a pasta local do repositório existir, é prudente verificar se algum arquivo foi alterado (usar o item 1.4.) e dependendo do que for listado, tomar a melhor decisão em relação a essa pasta local
>> **b.1)** se a deleta
>> **b.2)** ou se examina as alterações e procede com um novo *commit*
>>
**3.2.** Realizar as manutenções
**3.3.** Executar o item 1.2.
**3.4.** Executar o item 1.5.
**3.5.** Executar o item 1.8.
> O repositório local está "*commitado*" no github
**
---
### 4. Comandos no terminal do VSCode ou PowerShell

**4.1.** Criar uma pasta local
>**Comando**
>```mkdir [nome-da-pasta]```

**4.2.** Deletar uma pasta local, inclusive com as subpastas
>**Comando**
>```Remove-Item -Path [pasta] -Recurse -Force -ErrorAction Stop```
>> **a)** Substituir [pasta] pelo nome da pasta

**4.3.** Listar pastas ocultas
>**Comando**
>```dir -hidden```
>> **a)** Com esse comando será possível ver a pasta oculta *.git*