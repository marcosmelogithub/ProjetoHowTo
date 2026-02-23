
<style>

/* ======================= */
/* Personalizar os headers */
/* ======================= */
h1 {
    color: #20B2AA;
    text-align: center;
    border-bottom: 3px solid #3498db;
    font-family: Tahoma, Geneva, Verdana, sans-serif;
}

h2 {
    color: #ffffff;
    padding: 0px 10px;
}

/* Subtítulos (H3) - Ex: Configuração do usuário */
h3 {
    color: #2980b9;
    border-left: 5px solid #2980b9;
    padding-left: 10px;
    font-weight: bold;
}

span {
   padding: 0px 15px;
}

.nivel2span {
   padding: 0px 30px;
}

/* Estiliza o "container" do código */
pre {
   background-color: #ADFF2F !important; /* Fundo estilo Dracula */
   border-radius: 8px;
   padding: 10px;
   border: none;
   margin-left: 40px; /* Define o tamanho do recuo */
   border-left: 3px solid #ccc; /* Opcional: ajuda a visualizar o recuo */
   box-shadow: 3px 3px 10px rgba(0,0,0,0.3);
   width: max-content;
  }

/* Estiliza a fonte do código */
code {
    font-family: 'Fira Code', 'Consolas', monospace;
    color: #f8f8f2;
    font-size: 0.95em;
  }

blockquote {
   background-color: #F08080 !important;
   border-radius: 8px;
   border-left: 4px solid #ddd;
   box-shadow: 2px 2px 5px rgba(0,0,0,0.05);
   width: max-content;
}

blockquote p {
    margin: 0;
}


.alturalinhabranca {
   line-height: 0.5; /* 2.0 significa o dobro do tamanho da fonte */
}

</style>

# GitHub Quick Guide

## 1. Novo Repositório no GitHub
   <span>1.1. Logar no Github</span>

   <span>1.2. Criar um novo repositório no GitHub</span>
   <blockquote>
      <b>Orientação Importante:</b><br>
      <b>a)</b> normalmente essa pasta é criada com o mesmo nome do repositório no GitHub<br>
      <b>b)</b> nessa pasta será onde os arquivos estarão temporariamente enquanto são alterados<br>
      <b>c)</b> após atualizar a branch principal no GitHub (com git push),<br> essa pasta poderá ser deletada, se desejar<br>
      <b>d)</b> a vantagem de deletar é que terá somente a última versão do projeto no GitHub,<br>
      minimizando, e até eliminando, assim um menor erro de confusão futuramente entre as versões<br>
      <b>e)</b> quando, no futuro, quiser trabalhar novamente no projeto,<br>
      bastará fazer um clone do Github para a máquina local, iniciando assim<br>
      exatamente do último ponto que foi publicado no GitHub
   </blockquote>

   <blockquote>
   <b>Orientação Importante:</b>
   <br>
   após criar o repositório no github, seguem as ações locais
   </blockquote>

   <span>1.3. Ações no repositório local</span>

   <span class="nivel2span">1.3.1. Criar uma pasta local</span>
   <span class="nivel2span">1.3.2. Ir para essa pasta local</span>
   
   <blockquote>
      <b>Orientação Importante:</b><br>
      os comandos abaixo devem ser dados por linha de comando,<br>
      seja no terminal do VSCode, PowerShell do Windows ou shell do Linux
   </blockquote>

   <span class="nivel2span">1.3.3. Iniciar o git com o comando</span>
   <pre>git init</pre>
   
   <blockquote>
      <b>Orientação Importante:</b><br>
      <b>a)</b>o comando init cria uma pasta oculta chamada ".git"<br>
      onde é realizado todo o gerenciamento de versão pelo git 
   </blockquote>

   <span class="nivel2span">1.3.4. Visualizar a pasta oculta criada pelo init</span>
   <pre>dir -hidden (terminal VSCode ou PowerShell)</pre>

   <span class="nivel2span">1.3.5. Criar o arquivo README.md:</span>
   <pre>touch README.md</pre>

   <span class="nivel2span">1.3.6. Adicionar o arquivo README.md ao controle de versão do Git:</span>
   <pre>git add README.md</pre>

   <span class="nivel2span">1.3.7. Realizar o commit do arquivo README.md</span>
   <pre>git commit -m "arquivo README.md criado"</pre>

   <span class="nivel2span">1.3.8. Associar com o branch no GitHub</span>
   <pre>git branch -M main</pre>
   
   <span class="nivel2span">1.3.9. Conectar com o branch main</span>
   <pre>git remote add origin https://github.com/[githubuser]/[nomerepositório].git
      <i>a) substituir [githubuser] pelo nome do seu usuário no GitHub e
      b) substituir [nomerepositório] pelo nome do repositório no github</i>
   </pre>

   <span class="nivel2span">1.3.10. Atualizar o branch principal no Github</span>
   <pre>git push -u origin main</pre>

   <span class="nivel2span">1.3.11. Deletar a pasta do repositório local</span>
   <pre>Remove-Item -Path [pasta] -Recurse -Force -ErrorAction Stop
   <i>a) substituir [pasta] pelo nome da pasta que será deletada</i>
   </pre>
## 2. Clonando Repositório do GitHub para local

<blockquote>
   <b>Orientação Importante:</b><br>
   <b>a)</b> A clonagem de repositório do GitHub para Local significa fazer uma cópia exata do<br>projeto para uma pasta local para que se possa fazer alterações, evoluções e testes.<br>
   <b>b)</b> Assim que tudo estiver alterado e testado, bastará atualizar o projeto no GitHub<br> para uma próxima clonagem.  
</blockquote>

<span>O comando git para clonagem é:</span>

<pre>
git clone https://github.com/[githubuser]/[nomerepositório].git 
</pre>

<blockquote>
   <b>Orientação Importante:</b><br>
   <b>a)</b>O comando clone irá criar uma pasta com o mesmo nome do repositório.<br>
   <b>b)</b>Caso deseje outro nome da pasta local, basta acrescentar o nome da pasta local no final<br> do comando clone  
</blockquote>

## 3. Sequência lógica de ações para manutenção de um projeto

<span>3.1. Clonar o repositório no github para uma pasta local</span>
<span>3.2. Se posicionar na pasta local</span>
<span>3.3. Realizar as manutenções e testes no projeto</span>
<span>3.4. Adicionar os arquivos alterados ao git (1.3.6)</span>
<span>3.5. Realizar o commit dos arquivos alterados (1.3.7)</span>
<span>3.6. Realizar atualização do repositório no github (1.3.10)<span>
<span>3.7. Deletar a pasta local (1.3.11)</span>

## 4. Restaurando arquivos

<blockquote>
. O git oferece o recurso de restaurar repositórios inteiros ou mesmo um arquivo específico<br>
. Abaixo seguem as situações de restore
</blockquote>

<span>4.1. Restaura um arquivo do último commit no github e substitui o atual na pasta local</span>
<pre>
git restore [nome-do-arquivo]<br>
<b>a)</b> substituir o [nome-do-arquivo] pelo nome do arquivo que se deseja restaurar
<b>b)</b> o arquivo a ser restaurado tem que existir no últinmo commit no github
</pre>

<span>4.2. Restaura um arquivo de qualquer commit anterior ao atual no github</span>
<pre>
git restore --source=[hash] [arquivo-restaurar]<br>
<b>a)</b> [hash] é o id do arquivo que está "commitado" em algum commit no github
<b>b)</b> [arquivo-restaurar] é o nome do arquivo que se deseja restaurar
</pre>

<span class="nivel2span">4.2.2. obtendo os hash do arquivo nos commit´s no github</span>
<pre>git log --pretty=format:"%h - %ad : %s" [nome-arquivo]</pre>
<blockquote>
A listagem será em ordem decrescente por commit, ou seja, a primeira linha corresponde ao<br>commit atual, a 2a linha, se houver, ao commit anterior, e assim por diante até<br>listar o primeiro commit
</blockquote>
<blockquote>
Por exemplo o comando<br>
<span class="nivel2span"><b><i>git log --pretty=format:"%h - %ad : %s" README.md</i></b></span></br>
resultará na lista:<br>
<span class="nivel2span"><b><i>70680f1 - Sun Feb 22 20:17:20 2026 -0300 : 1a alteração no repositório</i></b></span><br>
<span class="nivel2span"><b><i>207bf39 - Sun Feb 22 19:45:41 2026 -0300 : README.md criado</i></b></span><br>
sendo, <b><i>70680f1</i></b> e <b><i>207bf39</b><i> as hashes dos commits
</blockquote>
<blockquote>
<b>a)</b> Se no comando <i>git log</i> não indicar o nome do arquivo, trará a lista de todos commits no github<br>
<b>b)</b> Se indicar o nome do arquivo, trará todos os commits que o arquivo foi atualizado
</blockquote>

<span>4.3. Restaura todo o repositório do último commit no github</span>
<pre>git restore .</pre>

<span>4.4. Desfaz o git add</span>
<pre>git restore --staged [nome-arquivo]</pre>
<blockquote>
<b>a)</b> quando executa um <i>git add</i>, o arquivo é adicionado na lista (stage) para commit<br>
<b>b)</b> se desistir e quiser retirar o arquido da fila, basta executar o comando acima
</blockquote>

<span>4.5. Lista os arquivos "<i>staged</i>"</span>
<pre>git status</pre>