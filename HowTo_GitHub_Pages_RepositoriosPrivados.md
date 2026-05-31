# GitHub Pages x Repositórios Privados

## Entendendo o problema

* A ideia base é gerar uma página web para consultar o repositório privado no Github e exibir o conteúdo do arquivos do repositório sem expor o link direto do repositório/arquivo

Abaixo seguem as considerações para resolver essa demanda

---
## Entendendo se o Github aceita links invisíveis
---
**Não da forma exata como você imaginou (por link secreto), mas sim através de uma alternativa oficial e segura.**

<br>
No GitHub, **não existe o conceito de "link invisível"** (como acontece no Google Drive ou no YouTube, onde qualquer um com o link acessa um arquivo não listado). No GitHub, ou o repositório é 100% Público (qualquer pessoa na internet acha e lê) ou é 100% Privado.

<br>
Para fazer exatamente o que você quer — permitir o acesso **apenas de pessoas específicas, somente para leitura** —, você deve usar um **Repositório Privado** e gerenciar os acessos.

<br>
Aqui está como funciona e como configurar na prática:

### Como funciona o acesso somente leitura em repositórios privados
Quando você cria um repositório privado, ninguém consegue vê-lo, nem mesmo se tiver o link direto (o GitHub mostrará uma página de "Erro 404 - Não encontrado").

<br>
Para dar acesso a alguém, você precisa **adicionar o e-mail ou o nome de usuário do GitHub** dessa pessoa como colaborador e definir a permissão dela como **Read (Leitura)**.

#### Passo a Passo para Configurar:
 1. Crie o repositório como Privado
   No GitHub
   Ao criar o repositório, certifique-se de marcar a opção Private.
 2. Vá em Configurações (Settings)
   Menu lateral esquerdo
   Dentro do repositório criado, clique na aba Settings (ícone de engrenagem na barra superior).
 3. Acesse 'Collaborators'
   Gerenciar acesso
   No menu esquerdo, clique em Collaborators (será necessário confirmar a sua senha do GitHub).
 4. Clique em 'Add people'
   Botão verde
   Digite o e-mail ou o @username da pessoa que você deseja autorizar.
 5. Mude a permissão para 'Read'
   Atenção crucial aqui
   Antes de enviar o convite, clique no menu suspenso de permissões (que por padrão vem como Write) e altere para Read. Depois, clique em Add [Nome] to this repository.

>Pronto! A pessoa receberá um link por e-mail para aceitar o convite. Assim que ela aceitar, ela poderá ler todo o código, baixar os arquivos e clonar o repositório, mas **nunca conseguirá alterar nada ou enviar códigos (fazer Push)** para o seu projeto.
#
## Uma alternativa se você NÃO quiser exigir conta no GitHub: GitHub Pages
Se o seu objetivo é que as pessoas leiam apenas o *resultado final* do seu projeto (como um site, uma documentação ou um portfólio) e você não quer obrigá-las a ter uma conta no GitHub, você pode:
 1. Manter o código do seu repositório como **Privado**.
 2. Ativar o **GitHub Pages** (disponível em *Settings > Pages*).
Isso gerará um link público para o site hospedado, mas o seu código-fonte por trás dele continuará completamente invisível e privado.

---
## Explorando o uso de uma página construída com html, css e js
---
**Sim, você compreendeu perfeitamente a lógica**, mas com um **detalhe de segurança crucial** que você precisa saber sobre o JavaScript nesse cenário.
Para o visitante comum do site, o seu código-fonte original no GitHub (histórico de alterações, abas de commits, problemas do projeto, etc.) estará totalmente escondido e inacessível através da plataforma do GitHub. Porém, a dinâmica dos arquivos do site funciona exatamente como você descreveu.

<br>
Abaixo, veja como essa estrutura se comporta na prática e onde mora o perigo no uso do JavaScript:

### 1. Como os arquivos do repositório ficam expostos?
Quando o GitHub Pages compila um repositório privado para gerar um link de site público, **todos os arquivos estáticos dentro da pasta de publicação tornam-se públicos na web**, contanto que a pessoa saiba o caminho exato deles.
 * Se você tiver um arquivo chamado segredo.txt na raiz do repositório, ele não aparecerá em menus do seu site de forma automática.
 * No entanto, se qualquer pessoa digitar no navegador www.seusite.com/segredo.txt, o navegador **vai abrir e ler o arquivo**, porque o GitHub Pages o publicou no servidor.

### 2. O perigo do código JavaScript puro (Frontend)
Se você criar um código JavaScript dentro do seu site (usando fetch() por exemplo) para ler um arquivo de texto ou JSON guardado dentro desse mesmo repositório e injetar o conteúdo na tela, qualquer usuário comum poderá:
 1. Ver o conteúdo que o JavaScript puxou na tela do site.
 2. Abrir o "Modo de Inspeção" do navegador (tecla F12), olhar a aba "Network" (Rede) ou "Sources" (Fontes) e ler o código JavaScript para descobrir de qual arquivo o site está puxando os dados.
Ou seja: o JavaScript consegue sim acessar os arquivos e mostrar no site, mas ele **não esconde os caminhos desses arquivos** de usuários maliciosos ou curiosos.
## Resumo Visual do Fluxo de Acesso
Como ilustrado acima, o acesso é segmentado em duas barreiras completamente isoladas:
| Tipo de Acesso | O Usuário comum consegue fazer? | Explicação Técnica |
|---|---|---|
| **Acessar o Repositório no GitHub.com** | **NÃO ❌** | Se o usuário tentar acessar github.com/seu-usuario/seu-repositorio, ele verá uma tela de erro 404 (Página não encontrada). O seu código e histórico continuam protegidos. |
| **Acessar o site público** | **SIM | O link do GitHub Pages gera um site estático aberto para qualquer pessoa no mundo visualizar o HTML, CSS e JavaScript compilados. |
| **Baixar arquivos que o site usa** | **SIM | Se o site lê um arquivo usando JavaScript, esse arquivo foi enviado para o servidor público do site. Logo, o visitante consegue deduzir a URL dele. |

### Uma observação técnica importante sobre planos
Vale destacar uma regra comercial do GitHub: a função de criar um **site público** (GitHub Pages) a partir de um **repositório privado** não está disponível nas contas gratuitas (*GitHub Free*).

<br>
Para conseguir fazer essa combinação exata, você precisa de uma assinatura **GitHub Pro, GitHub Team** ou usar uma conta de organização corporativa.

<br>
Se você estiver na conta gratuita e tentar ativar o GitHub Pages, o GitHub forçará o repositório a se tornar público primeiro.

<br>
*(Caso precise fazer isso de graça com repositório privado, a alternativa recomendada é hospedar o seu código privado no GitHub e conectar o repositório a serviços gratuitos de terceiros como o **Vercel** ou **Netlify**, que geram o link do site público sem cobrar nada por repositórios privados).*

---
## Superando a restrição de segurança do js
---
Para resolver esse problema de forma **100% segura**, você precisa mudar a estratégia: o JavaScript do seu site não pode mais ir buscar o arquivo diretamente.

<br>
Se o arquivo segredo.txt for enviado para o servidor do GitHub Pages, ele sempre será público para quem souber a URL. Portanto, a única forma de torná-lo inacessível via URL direta é **não publicando o arquivo no site**, deixando-o guardado a sete chaves apenas dentro do repositório privado.

<br>
Para exibir o conteúdo dele na tela sem expor o arquivo, você precisa de uma **API intermediária (Backend)** que faça o papel de "segurança da festa": ela vai até o repositório privado, pega o texto, e entrega apenas o texto limpo para o seu JavaScript.

<br>
A melhor tecnologia gratuita e moderna para fazer isso hoje em dia são as **GitHub Actions** combinadas com uma técnica de compilação (Static Site Generation).

### A Solução Mais Segura: Injeção de Conteúdo via GitHub Actions
Em vez de o JavaScript buscar o arquivo quando o usuário abre o site, um robô do GitHub (a Action) lê o arquivo privado **antes** do site ir para o ar, copia o texto dele e o janta (injeta) direto dentro do código HTML. O arquivo segredo.txt nunca é publicado na internet.
### Como estruturar o seu código:

#### 1. O seu arquivo HTML (index.html)
No seu HTML, você não usará JavaScript para fazer fetch. Você deixará apenas uma marcação (um "molde") onde o texto deve entrar:
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Meu Site Seguro</title>
</head>
<body>
    <h1>Conteúdo Restrito:</h1>
    <div id="conteudo-secreto">{{CONTEUDO_SECRETO}}</div>
</body>
</html>

```
#### 2. O Script de Automação (compilar.js)
Você criará um pequeno script em Node.js no seu repositório privado. Esse script vai ler o arquivo secreto localmente e substituir a marcação {{CONTEUDO_SECRETO}} pelo texto real dentro do HTML.
```javascript
const fs = require('fs');

// 1. Lê o conteúdo do arquivo privado que NUNCA vai para a web
const conteudoSecreto = fs.readFileSync('segredo.txt', 'utf8');

// 2. Lê o molde do seu arquivo HTML
let html = fs.readFileSync('index.html', 'utf8');

// 3. Substitui a marcação pelo conteúdo real
html = html.replace('{{CONTEUDO_SECRETO}}', conteudoSecreto);

// 4. Salva o HTML final pronto que será enviado ao servidor
fs.writeFileSync('dist/index.html', html);

```
#### 3. O Fluxo do GitHub (.github/workflows/deploy.yml)
Você configura o GitHub para rodar esse script toda vez que você atualizar o repositório. Ele vai gerar a pasta dist (que contém apenas o HTML modificado) e publicará **apenas a pasta dist** no GitHub Pages.
### Por que essa abordagem é 100% segura?
 1. **O arquivo segredo.txt não existe no servidor do site:** Se alguém tentar acessar seusite.com/segredo.txt, receberá um erro 404 (Não encontrado), porque o arquivo simplesmente não foi enviado para lá.
 2. **Não há rastros no JavaScript:** O visitante do site pode abrir o modo de inspeção (F12) e revirar o código; tudo o que ele verá é o texto já escrito no HTML. Ele não saberá se aquele texto veio de um arquivo de texto, de um banco de dados ou se você o digitou manualmente.
 3. **Proteção do código-fonte:** O script que faz a mágica (compilar.js) e o arquivo original (segredo.txt) permanecem protegidos pelas credenciais do seu repositório privado no GitHub.

 ---
 ## Github Pages com repositório privado: somente no github pago - planos github e alternativas gratuítas
 ---
Para hospedar um site no **GitHub Pages** utilizando um **repositório privado**, o GitHub exige que você tenha uma assinatura paga.

<br>
Atualmente, o GitHub oferece três planos principais que desbloqueiam esse recurso para usuários individuais e empresas. Abaixo estão os planos, seus valores e para quem cada um é indicado:

### 1. GitHub Pro
Este é o plano ideal para **desenvolvedores autônomos ou profissionais independentes** que precisam de recursos avançados sem estarem vinculados a uma grande organização.
 * **Preço:** $4 por mês (ou $48 no plano anual).
 * **O que inclui além do Pages Privado:** * 3 GB de armazenamento em repositórios privados (para pacotes e arquivos).
   * **180 Core-hours** por mês no GitHub Codespaces (em vez das 120 horas do plano gratuito).
   * Ferramentas avançadas de revisão de código e gráficos de contribuição detalhados.
### 2. GitHub Team
Este plano é voltado para **pequenas e médias equipes de desenvolvimento** que precisam gerenciar permissões de membros, projetos conjuntos e segurança de forma centralizada.
 * **Preço:** $4 por usuário/mês (mínimo de $16/mês para pequenas equipes, escalando conforme o número de membros).
 * **O que inclui além do Pages Privado:**
   * 4 GB de armazenamento em repositórios privados por usuário.
   * Gerenciamento de equipes, níveis de acesso e suporte técnico com resposta em até 24h.
   * Mais minutos de execução para automações (GitHub Actions).
### 3. GitHub Enterprise
O plano topo de linha, desenhado para **grandes empresas, corporações e multinacionais** que exigem segurança de nível militar, conformidade regulatória e auditoria.
 * **Preço:** $21 por usuário/mês (faturamento corporativo geral).
 * **O que inclui além do Pages Privado:**
   * 50 GB de armazenamento para pacotes.
   * Controle de acesso via Single Sign-On (SAML/SSO), permitindo integrar as contas dos funcionários ao sistema de login da empresa.
   * Suporte premium 24/7 e suporte para servidores internos (GitHub Enterprise Server).

### 💡 Uma Alternativa 100% Gratuita (Sem assinar planos)
Se você não quer ou não pode investir em um plano pago do GitHub agora, existe um "truque" de mercado muito utilizado por desenvolvedores. Você pode manter o seu código **totalmente privado no plano gratuito do GitHub** e fazer a hospedagem do site em plataformas parceiras que oferecem Pages privado de graça:
 * **Vercel** ou **Netlify:** Você cria uma conta gratuita nelas, conecta o seu repositório privado do GitHub e elas geram o link do site público. Toda vez que você atualiza o código no GitHub, o site atualiza sozinho. É seguro, rápido e não custa nada.

---
## Uso de domínio próprio
---

**Sim, todas as três plataformas suportam domínios próprios** e, o melhor de tudo: de forma **100% gratuita**.

<br>
Nenhuma delas cobra taxas extras para você tirar aquele endereço padrão (como seu-site.vercel.app ou seu-site.github.io) e colocar o seu próprio (como www.seusite.com).

<br>
Além disso, todas elas geram o certificado de segurança (HTTPS/Cadeado verde) automaticamente e sem custo.

<br>
Aqui está como funciona o suporte a domínio próprio em cada uma:

### 1. GitHub Pages (com Domínio Próprio)
Como vimos antes, se o seu repositório for **público** (no plano gratuito) ou **privado** (nos planos Pro/Team), você pode ir nas configurações do repositório e digitar o seu domínio.
 * **Como é feita a configuração:** Exatamente igual ao processo do Blogger. Você vai até o painel da empresa onde comprou o domínio (Registro.br, GoDaddy, etc.) e aponta um registro **CNAME** para o endereço do seu perfil do GitHub (ex: seu-usuario.github.io) e adiciona os IPs do GitHub em registros do Tipo A.
### 2. Vercel (com Domínio Próprio)
A Vercel é uma das plataformas mais modernas e fáceis de configurar do mercado. Ela é ideal se você optou por deixar o seu código **privado e gratuito** no GitHub.
 * **Como é feita a configuração:** Dentro do painel da Vercel, nas configurações do seu projeto, você clica em "Domains" e digita o seu domínio.
 * **O diferencial:** A Vercel tem um sistema inteligente. Assim que você digita o domínio, ela analisa o seu provedor e te dá exatamente as linhas que você precisa copiar. Geralmente, ela pede apenas um registro **CNAME** apontando para cname.vercel-dns.com ou um registro **A** apontando para o IP deles. A verificação costuma ser extremamente rápida.
### 3. Netlify (com Domínio Próprio)
A Netlify funciona de forma muito parecida com a Vercel e também aceita repositórios privados do GitHub de graça.
 * **Como é feita a configuração:** No painel do projeto na Netlify, você vai em *Domain Management* e adiciona o seu endereço. Você pode configurar apontando o CNAME para o domínio interno deles (ex: seu-site.netlify.app).
 * **O diferencial (Netlify DNS):** A Netlify oferece uma opção extra muito confortável para iniciantes. Você pode alterar os "Nameservers" (servidores de nome) no seu provedor de domínio para os da Netlify. Fazendo isso, a Netlify passa a gerenciar todo o seu domínio, e você não precisa mais ficar mexendo em tabelas de DNS complexas no site onde comprou o domínio.
### Resumo: Qual escolher?
Se você quer manter o seu projeto **gratuito e com código privado**, a combinação perfeita é:
> **Código no GitHub (Privado) + Hospedagem na Vercel ou Netlify + Seu Domínio Próprio.**
> 
O fluxo de atualização continua profissional: você altera o código no seu computador, envia para o GitHub, a Vercel/Netlify percebe a mudança, roda os scripts de segurança que criamos na resposta anterior e atualiza o seu domínio próprio em segundos.
