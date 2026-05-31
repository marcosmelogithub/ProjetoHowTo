# GitHub CodeSpace

## O que é o Codespace

O **GitHub Codespaces** é, de forma simples, um computador de programador que roda inteiramente na nuvem (na infraestrutura da Microsoft/GitHub) e que você pode acessar direto pelo seu navegador de internet ou pelo VS Code local.
Em vez de você gastar horas instalando programas, configurando variáveis de ambiente, baixando o banco de dados e preparando a sua máquina física para conseguir rodar o código de um projeto, o Codespaces cria um **ambiente de desenvolvimento completo, isolado e pré-configurado** em poucos segundos dentro de um container na nuvem.
### Qual a finalidade prática dele?
No dia a dia do desenvolvimento de software, o Codespaces resolve problemas reais muito comuns. As principais aplicações práticas são:
#### 1. Acabar com o "Na minha máquina funciona"
Esse é um dos maiores clássicos da programação: um código funciona perfeitamente no computador de um desenvolvedor, mas quebra no do outro porque as versões do Node.js, Python ou do sistema operacional são diferentes.
 * **A aplicação prática:** O Codespaces usa um arquivo de configuração (chamado devcontainer.json). Quando qualquer pessoa da equipe abre o projeto no Codespaces, o GitHub cria uma máquina virtual idêntica para todo mundo, com as mesmas extensões, ferramentas e versões. O ambiente se torna padronizado.
#### 2. Programar de qualquer lugar (e de qualquer dispositivo)
Como o processamento pesado e o armazenamento acontecem nos servidores da nuvem, o desempenho do seu computador físico se torna irrelevante.
 * **A aplicação prática:** Você pode abrir um projeto pesado de Inteligência Artificial ou um site complexo usando um notebook super antigo, um Chromebook ou até mesmo um **iPad/Tablet** na praia. Se o aparelho abrir o navegador Google Chrome, você consegue programar com a mesma velocidade de um computador de última geração.
#### 3. Integração imediata de novos programadores (Onboarding)
Quando um programador entra em uma empresa ou vai colaborar em um projeto de código aberto (Open Source), ele costuma perder o primeiro dia inteiro apenas configurando o computador.
 * **A aplicação prática:** Com o Codespaces, o novo desenvolvedor entra na página do repositório no GitHub, clica em um botão verde escrito "Create codespace" e, em menos de dois minutos, uma tela idêntica ao VS Code se abre com o projeto pronto para rodar, testar e debugar.
#### 4. Revisão de código rápida (Code Review)
Se você precisa testar uma alteração que um colega de trabalho fez (um Pull Request), normalmente você teria que parar o que está fazendo na sua máquina, trocar de branch no Git, baixar as dependências dele, testar e depois voltar para o seu trabalho.
 * **A aplicação prática:** Você pode abrir o código do seu colega em um Codespace separado na nuvem, testar as alterações dele no navegador e, quando terminar, fechar a aba. O seu computador local continuou intacto e você não perdeu o foco do seu próprio código.

---
## Entendendo os limites do codespace
----
O limite de tempo de uso do **GitHub Codespaces** depende do tipo de conta que você possui. O cálculo é feito mensalmente em **horas de núcleo (Core Hours)**, o que significa que o tempo real de uso muda conforme a potência da máquina virtual que você escolhe.
Os limites gratuitos mensais são:
 * **Conta GitHub Free (Gratuita):** **120 horas de núcleo** por mês.
 * **Conta GitHub Pro / Student Pack:** **180 horas de núcleo** por mês.
### Como funciona o cálculo de tempo (Core Hours)?
As horas de núcleo não equivalem necessariamente a "horas de relógio". O tempo disponível é dividido pela quantidade de processadores (cores) da máquina virtual que você está rodando:
| Tipo de Máquina | Equivalência no Plano Free (120 Core Hours) |
|---|---|
| **Máquina básica (2 cores)** | **60 horas reais** de uso no mês |
| **Máquina intermediária (4 cores)** | **30 horas reais** de uso no mês |
| **Máquina avançada (8 cores)** | **15 horas reais** de uso no mês |
> 💡 **Nota:** Por padrão, o Codespaces inicia projetos em máquinas de 2 cores, garantindo a você cerca de **60 horas** de programação no ambiente em nuvem.
> 
### O Limite "Invisível": Armazenamento
Além do tempo de uso da máquina ligada, o GitHub oferece uma cota mensal de armazenamento para salvar os seus ambientes (arquivos, extensões instaladas, etc.):
 * **GitHub Free:** 15 GB por mês.
 * **GitHub Pro:** 20 GB por mês.
> ⚠️ **Atenção:** Seus ambientes consomem essa cota de armazenamento **mesmo quando o Codespace está desligado**. Se você deixar muitos projetos antigos criados na sua conta, eles gastarão todo o seu limite de Gigabytes, impedindo você de abrir novos Codespaces mesmo que ainda tenha horas de uso disponíveis.
> 
### 3 Dicas Práticas para Economizar suas Horas
 1. **Reduza o tempo de inatividade (Idle Timeout):** Por padrão, o Codespaces fica ligado por 30 minutos sem uso antes de desligar sozinho. Vá nas configurações do seu GitHub e reduza esse tempo para 10 ou 15 minutos para evitar desperdício.
 2. **Delete projetos antigos:** Acesse [github.com/codespaces](https://github.com/codespaces) regularmente e exclua os ambientes que você já finalizou para liberar os 15 GB de armazenamento.
 3. **Use a máquina de 2 cores:** A menos que esteja compilando um projeto extremamente pesado, a máquina padrão é mais do que suficiente e faz suas horas renderem o dobro.

---
## Identificando os codespaces ativos
---
Para visualizar quais repositórios possuem ambientes do Codespaces ativos ou criados na sua conta, existem duas formas práticas: pelo **navegador (site do GitHub)** ou por **linha de comando (Terminal/CLI)**.
Aqui está o passo a passo para cada uma delas:
## Método 1: Pelo Navegador (O jeito mais fácil)
O GitHub centraliza todos os seus ambientes virtuais em um painel de controle único.
 1. Acesse o site do GitHub e faça login na sua conta.
 2. No canto superior direito, clique na sua **foto de perfil**.
 3. No menu suspenso, clique em **Your codespaces** (ou acesse direto o endereço github.com/codespaces).
Nessa tela, você verá uma lista de todos os seus Codespaces ativos e inativos. Cada item da lista mostra:
 * O nome do repositório ao qual ele pertence.
 * O status atual (ex: *Available*, *Active*, *Stopped*).
 * Há quanto tempo ele foi usado pela última vez.
 * A quantidade de armazenamento que ele está consumindo.
## Método 2: Pelo Terminal (Para quem já está programando)
Se você já usa a ferramenta de linha de comando oficial do GitHub (o **GitHub CLI** ou simplesmente gh), você pode listar seus ambientes direto pelo terminal do seu computador.
 1. Abra o seu terminal.
 2. Digite o seguinte comando e aperte Enter:
```bash
gh codespace list

```
O terminal retornará uma tabela organizada com o nome do codespace, o repositório vinculado, o estado atual (se está rodando ou desligado) e a data da última atualização.
### 💡 Dica Importante sobre o Status
 * **Active/Running:** O ambiente está ligado e consumindo suas horas mensais do plano.
 * **Stopped/Shutdown:** O ambiente está desligado. Ele **não** está gastando suas horas de uso, mas continua consumindo a sua cota de armazenamento (os 15 GB gratuitos) até que você clique nos três pontinhos ao lado dele e selecione **Delete**.
