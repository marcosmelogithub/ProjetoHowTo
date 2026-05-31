# Blogger

## O Blogger
O **Blogger** é uma das plataformas de gerenciamento de conteúdo (CMS) mais antigas e conhecidas da internet. Criado pela Pyra Labs em 1999 e comprado pela Google em 2003, ele foi um dos grandes responsáveis por popularizar a cultura dos blogs nos anos 2000, permitindo que qualquer pessoa publicasse textos na web sem precisar entender de programação.

<br>

Em termos simples: ele funciona como um sistema de diário ou revista eletrônica, onde você escreve as suas postagens através de um painel simples (parecido com o Microsoft Word) e o site organiza tudo automaticamente por ordem cronológica.

### Para que ele serve? (Aplicações Práticas)

Embora o WordPress domine o mercado de sites profissionais hoje em dia, o Blogger ainda tem um espaço muito forte devido à sua simplicidade e custo zero. Suas principais aplicações incluem:
 * **Blogs Pessoais e Diários Virtuais:** Perfeito para quem quer apenas escrever sobre o seu dia a dia, registrar viagens, compartilhar pensamentos ou criar um portfólio de textos.
 * **Portais de Conteúdo e Nicho:** Criação de sites de notícias locais, blogs de culinária, resenhas de livros, cinema ou tutoriais técnicos.
 * **Ganhar Dinheiro com Conteúdo (Monetização):** Por ser da Google, ele possui integração nativa e simplificada com o **Google AdSense**. Isso permite que blogueiros exibam anúncios em suas páginas e ganhem dinheiro por visualizações ou cliques de forma muito fácil.
 * **Ambiente Educacional:** Muitos professores utilizam o Blogger para criar páginas de turmas, publicar materiais de apoio, cronogramas de aulas e centralizar trabalhos dos alunos.
### Principais Vantagens do Blogger
> **O grande diferencial:** No Blogger, a hospedagem do site é 100% gratuita e mantida nos servidores da Google. Você não precisa pagar mensalidades para manter o seu site no ar, mesmo que ele receba milhares de acessos.
> 
 * **Domínio personalizado grátis:** Você pode usar o endereço gratuito deles (ex: seusite.blogspot.com) ou comprar um domínio próprio (ex: seusite.com) e conectá-lo sem pagar nenhuma taxa extra para a plataforma.
 * **Segurança Google:** Como o sistema roda nos servidores da Google, o seu site dificilmente vai cair por excesso de acessos e está altamente protegido contra ataques de hackers, sem que você precise instalar plug-ins de segurança.
 * **Curva de aprendizado baixa:** Você cria uma conta usando o seu próprio Gmail e, em menos de 5 minutos, o seu blog está configurado e pronto para receber o primeiro texto.

----

## Criando um template personalizado

Criar um template personalizado para o Blogger (Blogspot) exige um pouco de conhecimento em **HTML, CSS** e nas **tags específicas do Blogger** (que usam XML). O segredo é que o Blogger não aceita um arquivo HTML comum; ele precisa de uma estrutura que o servidor da Google consiga ler para puxar os seus posts de forma dinâmica.
Aqui está o passo a passo lógico para construir o seu próprio template do zero ou modificar um existente.

### Estrutura Básica Obrigatória

Todo template do Blogger precisa seguir esta espinha dorsal em XML. Se você tentar enviar um arquivo sem esses elementos, o Blogger retornará um erro.

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
  <head>
    <title><data:blog.pageTitle/></title>
    
    <b:skin><![CDATA[
      /* Todo o seu código CSS (estilização) entra aqui */
      body {
        background-color: #f5f5f5;
        font-family: Arial, sans-serif;
      }
    ]]></b:skin>
  </head>
  
  <body>
    <!-- A estrutura visual do seu site entra aqui -->
    
    <!-- Seção obrigatória para o Blogger aceitar o código -->
    <b:section id='main-section' showaddelement='yes'>
      <!-- O Blogger exige pelo menos um widget dentro da seção -->
      <b:widget id='Blog1' locked='false' title='Postagens do blog' type='Blog' version='1'/>
    </b:section>
  </body>
</html>

```
### Entendendo os Componentes Principais
Para personalizar o layout, você precisa dominar três conceitos do Blogger:
 * **<b:skin>**: É onde fica o CSS. O Blogger compila o que está aqui dentro antes de enviar para o navegador.
 * **<b:section>**: São as "gavetas" do seu layout (ex: Cabeçalho, Barra Lateral, Corpo). Elas delimitam onde o usuário poderá arrastar e soltar elementos na aba "Layout" do painel.
 * **<b:widget>**: São os elementos reais (Componente de Posts, Marcadores, Perfil). Eles obrigatoriamente precisam estar dentro de uma <b:section>.
### Como Criar e Aplicar o seu Template
 1. Crie o arquivo localmente
   Use um editor de código
   Abra um editor de texto técnico (como VS Code, Notepad++ ou Sublime Text). Cole a estrutura básica em XML mostrada acima e salve o arquivo com a extensão .xml (ex: meu-template.xml).
 2. Faça backup do blog atual
   Segurança em primeiro lugar
   Acesse o painel do Blogger, vá em Tema, clique na seta ao lado de "Personalizar" e selecione Fazer backup. Baixe o arquivo atual para o seu computador caso precise reverter.
 3. Abra o editor HTML do Blogger
   Acesso direto ao código
   No mesmo menu suspenso ao lado de "Personalizar", clique em Editar HTML. Você verá o código do seu tema atual.
 4. Substitua o código
   Limpar e colar
   Selecione todo o código existente no Blogger (Ctrl+A) e apague-o. Abra o seu arquivo .xml criado no Passo 1, copie todo o conteúdo e cole dentro do editor do Blogger.
 5. Salve e teste
   Validação do servidor
   Clique no ícone de Salvar (um disquete no canto superior direito). Se o código tiver algum erro de tag aberta ou sintaxe XML, o Blogger avisará na hora. Se salvar com sucesso, visite o seu blog para ver a estrutura básica aplicada.
### Dicas para Avançar na Personalização
Como o desenvolvimento do zero pode ser trabalhoso devido às tags proprietárias do Blogger, a maioria dos designers prefere o caminho da **engenharia reversa**:
> **Dica de ouro:** Baixe um template gratuito que tenha uma estrutura limpa e responsiva (como os temas do *Sora Templates* ou *Gooyaabi Templates*). Abra o arquivo XML dele e comece alterando apenas as cores e fontes dentro do CSS (<b:skin>). É a forma mais rápida de aprender como as seções se comportam na prática.
> 

----
## Configurando domínio próprio no Blogger

Configurar um domínio próprio (como [www.seusite.com](https://www.seusite.com) em vez de seusite.blogspot.com) é o passo mais importante para dar uma cara profissional ao seu blog.
O processo é dividido em duas partes: você avisa o Blogger sobre o novo endereço, pega os códigos de verificação dele e depois insere esses códigos na empresa onde você comprou o domínio (Registro.br, GoDaddy, Namecheap, etc.).
### Parte 1: Gerando as chaves de verificação no Blogger
 1. Acesse as configurações
   No painel do Blogger
   No menu lateral esquerdo, clique em Configurações e role a página até a seção chamada Publicação.
 2. Insira o seu domínio
   Atenção ao detalhe
   Clique em Domínio personalizado. Digite o seu endereço obrigatoriamente começando com www (exemplo: [www.meusite.com](https://www.meusite.com).br) e clique em Salvar.
 3. Copie os dados do erro
   Aparecerá um aviso vermelho
   O Blogger vai recusar o salvamento e mostrará uma mensagem com dois códigos CNAME (eles são as chaves de segurança provando que você é o dono do domínio). Anote ou tire um print dessa tela, pois você usará os dados agora.
O aviso mostrará duas linhas parecidas com isto:
 * **CNAME 1:** Nome/Host: www | Destino: ghs.google.com
 * **CNAME 2:** Nome/Host: X7YZaBc... (um código aleatório) | Destino: gv-XXXX.dv.googlehosted.com (outro código longo)
### Parte 2: Configurando a Zona DNS no seu Provedor
Agora, abra uma nova aba, faça login no site onde você comprou o domínio (ex: Registro.br, HostGator, GoDaddy) e localize a opção **Gerenciar DNS** ou **Zona de DNS** do seu domínio.
Você precisará adicionar **6 registros** ao todo para que o site funcione perfeitamente com e sem o "www".
#### 1. Adicione os 2 CNAMEs (Que você pegou no Passo 3)
Crie duas novas entradas do tipo **CNAME**:
 * **Primeiro CNAME:** No campo *Nome/Host* coloque www e no campo *Destino/Aponta para* coloque ghs.google.com.
 * **Segundo CNAME:** No campo *Nome/Host* cole aquele primeiro código aleatório gerado pelo Blogger e, no campo *Destino*, cole o código longo correspondente a ele.
#### 2. Adicione os 4 IPs do Google (Registros do Tipo A)
Para garantir que o leitor que digitar apenas meusite.com.br (sem o www) consiga entrar no seu blog, crie **4 novas entradas do tipo A**. O campo *Nome/Host* deve ficar **em branco** (ou preenchido apenas com um @, dependendo da empresa). No campo *Destino/IP*, crie uma linha para cada um destes IPs da Google:
```text
216.239.32.21
216.239.34.21
216.239.36.21
216.239.38.21

```
### Parte 3: Ativando no Blogger
Depois de salvar as alterações na sua empresa de domínios, as informações precisam ser espalhadas pela internet (processo chamado de **propagação de DNS**). Isso costuma levar de **15 minutos até 1 hora** (em casos raros, até 24h).
 1. Finalize o salvamento
   Volte ao painel do Blogger
   Acesse novamente Configurações > Domínio personalizado, digite o seu domínio com www e clique em Salvar. Se o DNS já tiver propagado, ele aceitará o domínio sem mostrar erros.
 2. Ative o redirecionamento
   Garante o acesso sem www
   Logo abaixo do campo do domínio, ative a chave Redirecionar domínio. Isso fará com que qualquer pessoa que digite site.com vá direto para [www.site.com](https://www.site.com).
 3. Ative a segurança HTTPS
   O cadeado verde do navegador
   Um pouco mais abaixo, ative as opções Disponibilidade de HTTPS e Redirecionamento de HTTPS. O Blogger emitirá um certificado de segurança gratuito para o seu domínio em alguns minutos.
> ⚠️ **Importante:** Se você usa registros do tipo **CAA** no seu domínio, lembre-se de adicionar uma permissão para letsencrypt.org na sua zona de DNS, caso contrário o Blogger não conseguirá gerar o seu certificado de segurança HTTPS de forma automática.
> 

### Importante: o domínio próprio não precisa ser estar associado à uma cont Google

O domínio não precisa ter nenhuma ligação prévia com a Google e pode ser comprado em qualquer empresa registradora do mercado.
O único requisito real é que a empresa onde você comprou o domínio permita que você **edite a Zona de DNS** (o que 99% delas fazem por padrão, como Registro.br, GoDaddy, HostGator, Namecheap, etc.).
#### Como o Blogger enxerga essa relação?
A conexão entre o seu domínio e o Blogger é feita puramente por meio de **linhas de código de texto** (aqueles registros CNAME e do Tipo A que configuramos na Zona de DNS).
 * O domínio pode ter sido comprado com o seu CPF e um e-mail do Outlook na GoDaddy.
 * O seu blog pode estar em um Gmail totalmente diferente.
No momento em que você insere a chave CNAME exclusiva dentro do painel de controle do seu domínio, você está provando para o robô da Google: *"Olha, eu tenho a senha de administração deste domínio, logo, eu sou o dono dele"*. Essa validação técnica é o que importa para o Blogger, não o cadastro ou a conta onde o domínio foi comprado.

-----
## Como evoluir o aprendizado do Blogger

Como o Blogger (Blogspot) utiliza uma linguagem proprietária baseada em XML misturada com HTML/CSS, o mercado de livros físicos sobre o assunto ficou obsoleto muito rápido. Hoje, nenhum livro impresso ensinará você a criar layouts modernos e responsivos para o Blogger.

<br>
O conhecimento profissional e avançado sobre a plataforma migrou inteiramente para **comunidades de desenvolvedores, canais especializados e documentações técnicas na web**.

<br>
As melhores referências e caminhos de estudo para dominar o Blogger profissionalmente — inclusive a parte pesada de programação de templates — estão divididas em três frentes:

### 1. Documentação Oficial e Guias Técnicos (Para aprender as Tags XML)
Para criar ou modificar um template de forma avançada, você precisa entender as tags que começam com b: (como <b:section>, <b:loop>, <b:if>).
 * **Blogger Code Documentation (GitHub):** Não existe um manual oficial em PDF da Google, mas a comunidade de desenvolvedores mantém repositórios no GitHub que funcionam como a "bíblia" do código do Blogger. Procurar por *"Blogger XML Documentation"* no GitHub revela guias detalhados de todas as tags de dados disponíveis (data:post.body, data:blog.pageType, etc.).
 * **Central de Ajuda do Blogger (Avançado):** A própria ajuda do Google tem uma seção dedicada exclusivamente a "Mudar o design do seu blog usando HTML". Ela fornece as regras básicas sobre como o código precisa ser estruturado para que o servidor salve o arquivo.
### 2. Canais e Portais de "Engenharia Reversa" (A melhor escola)
A comunidade internacional do Blogger é muito ativa, especialmente na Ásia e América Latina. Os melhores portais ensinam programação direto na prática (geralmente mostrando trechos de código para você colar e testar):
 * **Way2Themes, Sora Templates e Gooyaabi Templates:** Estes não são sites de cursos, mas sim as maiores fábricas de templates profissionais do mundo. O melhor jeito de aprender profissionalmente é baixar a versão gratuita de um tema deles, abrir o arquivo .xml no seu editor de código (como o VS Code) e estudar como eles organizaram o CSS e as seções de anúncios, widgets e posts responsivos.
 * **Tutoriais no YouTube (Foco em Desenvolvimento):** Canais voltados para Web Design oferecem cursos em vídeo gratuitos (basta pesquisar por *"Como criar template Blogger do zero"*). Eles são excelentes porque mostram visualmente o que acontece quando você altera uma linha de código XML dentro do painel.
### 3. Cursos Online (Foco na aplicação profissional)
Se o seu objetivo com "profissional" também envolve SEO (otimização para o Google), marketing e monetização:
 * **Udemy:** A plataforma possui cursos específicos como *"Como Criar Blogs Profissionais no Blogger"* e *"Curso de Blogspot para Afiliados"*. Eles ensinam a configurar o design (usando frameworks prontos para não ter que programar tudo do zero) e focam muito em como deixar o blog rápido para passar nos testes do Google e começar a faturar com o AdSense.
### O Roteiro de Estudos Ideal
Se você quer se tornar um especialista em customização de Blogger, o caminho mais eficiente é este:
 1. **Aprenda HTML5 e CSS3 básico:** Sem isso, você não conseguirá mexer na identidade visual do blog (cores, margens, fontes, grid).
 2. **Entenda a lógica de Condicionais do Blogger:** Aprenda a usar a tag <b:if cond='...'>. É ela quem diz para o código: *"Se o usuário estiver na página inicial, mostre o banner; se ele estiver dentro de um post, esconda o banner"*. Isso é o que separa um layout amador de um profissional.
 3. **Estude o framework Bootstrap integrado ao Blogger:** Os templates profissionais mais modernos usam a estrutura de código do Bootstrap dentro do código do Blogger para gerenciar o layout de forma que ele se adapte perfeitamente a celulares, tablets e computadores.
