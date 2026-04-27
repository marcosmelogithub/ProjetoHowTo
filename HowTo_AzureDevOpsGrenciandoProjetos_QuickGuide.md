# Azure Devops Quick Guide - Gerenciando Projetos
---

#### 1. O que é o Azure DevOps

---

#### 2. Projetos Preditivos/Waterfall/Cascata no Azure DevOps

Com certeza! Embora o Azure DevOps seja amplamente associado ao **Scrum** e ao **Kanban**, ele é flexível o suficiente para suportar metodologias **Preditivas (Waterfall/Cascata)**. 

O segredo está em como você configura o processo e utiliza as ferramentas de visualização. Aqui está como estruturar isso:

##### 2.1. Escolha do Processo Base
Ao criar um projeto, o Azure DevOps oferece quatro processos padrão. Para projetos preditivos, a melhor escolha é o **CMMI (Capability Maturity Model Integration)**.
* **Por que o CMMI?** Ele possui requisitos de documentação mais rigorosos e estados de "Change Request" e "Review" que se alinham melhor ao controle rígido de escopo do modelo tradicional.
* **Personalização:** Você pode (e deve) criar um processo herdado para renomear termos como "Backlog" para "EAP (Estrutura Analítica do Projeto)" ou "WBS", se preferir a nomenclatura clássica.

##### 2.2 Estrutura de Escopo (WBS/EAP)
No modelo preditivo, o planejamento é "top-down". Você pode usar a hierarquia nativa para representar os níveis da sua EAP:
1.  **Epics:** Representam as grandes Fases do projeto (ex: Iniciação, Planejamento, Execução).
2.  **Features:** Entregáveis principais dentro de cada fase.
3.  **Requirements/Tasks:** O trabalho detalhado que precisa ser executado.

##### 2.3. Cronograma e Caminho Crítico (Plans e Gantt)
O Azure DevOps não possui um gráfico de Gantt nativo ultra-robusto no Board padrão, mas você resolve isso de duas formas:
* **Delivery Plans:** É uma extensão nativa que permite visualizar o trabalho em uma linha do tempo, ideal para ver marcos (milestones) e dependências entre equipes.
* **Extensões da Marketplace:** Para um "feeling" real de MS Project (com caminho crítico e predecessoras), a maioria dos gestores utiliza extensões como o **"Gantt Chart"** ou o **"Portfolio Plans"**.

##### 2.4. Gestão de Dependências
Projetos tradicionais dependem fortemente da ordem das tarefas. No Azure DevOps, você utiliza os links do tipo **Predecessor/Successor**. 
* Se uma tarefa atrasa, você consegue visualizar o impacto nas tarefas sucessoras através das abas de dependência ou nos gráficos de Gantt instalados.

##### 2.5. Dashboards de Controle
Diferente do Burndown (foco ágil), você pode configurar widgets de **"Status de Consulta"** para monitorar:
* Percentual de conclusão por Fase.
* Total de horas estimadas vs. Realizadas.
* Registro de Riscos e Problemas (usando Work Items customizados).

##### 2.6. Resumo da Adaptação

| Ferramenta | Uso no Ágil | Uso no Preditivo (Tradicional) |
| :--- | :--- | :--- |
| **Backlog** | Lista prioritária de desejos | **EAP (Escopo Fechado)** |
| **Sprints** | Ciclos de desenvolvimento | **Marcos ou Fases do Cronograma** |
| **Boards** | Fluxo de valor contínuo | **Status de Aprovação de Entregas** |
| **Wiki** | Documentação colaborativa | **Plano de Gerenciamento do Projeto** |

>**Dica de ouro:**
>>Se você já utiliza o **Microsoft Project Professional**, existe uma integração (via add-in ou ferramentas de terceiros) que permite que você planeje no Project e "publique" as tarefas diretamente no Azure DevOps para que a equipe técnica as execute.

##### 2.7. Importando do MS-Project para o Azure DevOps

Sim, existem três formas principais de fazer essa importação, dependendo da complexidade do seu cronograma e da frequência com que você precisará atualizar os dados.

Aqui estão as opções, da mais simples para a mais robusta:

###### 2.7.1. Importação via Excel (A mais comum)
Como o Azure DevOps não lê arquivos `.mpp` diretamente, o caminho mais utilizado é usar o Excel como ponte.
* **No MS Project:** Copie as colunas essenciais (Título, Data de Início, Data de Término, Atribuição) e cole em uma planilha Excel.
* **No Azure DevOps:** Vá em **Boards > Queries** e use a opção **Import Work Items**.
* **Dica:** Você precisará mapear as colunas do Project para os campos do Azure (ex: "Task Name" vira "Title"). Para manter a hierarquia, você deve usar a estrutura de colunas "Title 1", "Title 2", etc., ou configurar os IDs de "Parent" manualmente após a importação.

###### 2.7.2. Suplemento Azure DevOps para Office (Integração Direta)
A Microsoft oferece um suplemento chamado **Azure DevOps Office Integration**. 
* **Como funciona:** Após instalado, o Excel ganha uma aba "Team". Você pode conectar o Excel diretamente ao seu projeto no Azure DevOps.
* **Vantagem:** Você cola os dados do Project no Excel e clica em **Publish**. Isso cria todos os itens de trabalho automaticamente no Azure DevOps respeitando a estrutura.
* **Nota:** Embora o suporte direto ao MS Project tenha sido descontinuado nas versões mais recentes em favor do Excel/CSV, este suplemento ainda é a ferramenta oficial para edições em massa.

###### 2.7.3. Extensões do Marketplace (Para manter o Gráfico de Gantt)
Se você quer que o Azure DevOps se comporte como o MS Project (exibindo predecessoras e cronograma visual), importar apenas as tarefas via Excel não será suficiente, pois o Azure nativo não "desenha" o Gantt automaticamente.
* **Solução:** Instale extensões como **Gantt Chart**, **Portfolio Plans** ou **Precursive**. 
* Algumas dessas ferramentas possuem importadores próprios que tentam preservar as relações de dependência (predecessoras) que você configurou no MS Project.

###### 2.7.4. Integração via API ou Ferramentas de Terceiros (Project Online)
Se você usa o **Project Online (ou Project para a Web)**, existem conectores via **Power Automate** ou ferramentas especializadas (como a *IUNEX* ou *WBS Gantt-Chart*) que sincronizam os dois ambientes em tempo real.

###### 2.7.5 Recomendação
Se for uma importação única para iniciar o projeto:
1. Instale o **Azure DevOps Office Integration**.
2. Prepare os dados no Excel vindo do Project.
3. Use a aba **Team** do Excel para publicar no Azure DevOps.

>**Atenção:**
>>O Azure DevOps não possui por padrão um campo de "Data de Início" e "Data de Término" para todos os itens (como User Stories). Você precisará usar os campos **Start Date** e **Target Date** que geralmente estão disponíveis em *Features* e *Epics*, ou configurar o processo do seu projeto para exibir esses campos nas *Tasks*.

##### 2.8. Gerenciando linha de base no Azure DevOps

Essa é uma das perguntas mais frequentes de quem migra do MS Project para o Azure DevOps. A resposta curta é: **Nativamente, não da forma "congelada" que o PMBOK sugere, mas existem formas eficazes de simular e controlar isso.**

No MS Project, a *Baseline* (Linha de Base) tira um "print" do cronograma para comparar o *Planejado vs. Realizado*. No Azure DevOps, os dados são fluidos. 

Aqui estão as três estratégias para ter esse controle:

###### 2.8.1. O Recurso de "Delivery Plans" (Visualização de Marcadores)
O Azure possui um recurso chamado **Delivery Plans**. Ele permite que você visualize a linha do tempo das suas Epics e Features.
* **Como usar como Baseline:** Você pode configurar "Markers" (Marcadores) com datas fixas que representam os marcos contratuais ou as datas da linha de base original. Se as barras das tarefas começarem a ultrapassar esses marcadores verticais, você tem o alerta visual de desvio de cronograma.

###### 2.8.2. Uso de Campos Customizados (A estratégia mais robusta)
Para um controle preditivo real, a recomendação técnica é personalizar o seu Processo (CMMI ou Inherited) para incluir campos específicos de Linha de Base.
* **Crie os campos:**
    * `Baseline Start Date`
    * `Baseline Finish Date`
* **Lógica:** No início do projeto, você preenche esses campos com as datas planejadas. Durante a execução, a equipe altera os campos nativos (`Start Date` e `Target Date`). 
* **Análise:** Você cria uma **Query** (Consulta) que subtrai a Data Real da Data da Linha de Base para gerar um relatório de variância (atraso em dias).

###### 2.8.3. Extensões de Gráfico de Gantt (Recomendado)
Para quem não quer configurar campos manuais, o Marketplace do Azure DevOps possui extensões como o **Gantt Chart** ou o **WBS Gantt-Chart** que possuem o botão **"Set Baseline"**.
* Essas ferramentas salvam o estado atual de todas as tarefas.
* Elas exibem uma barra cinza (a baseline) abaixo da barra colorida (o cronograma atual), permitindo ver visualmente o quanto o projeto "escorregou".

###### 2.8.4. O Histórico do Work Item (Auditoria)
Diferente de um arquivo de Excel, o Azure DevOps guarda o histórico de **cada alteração** feita em uma data.
* Se alguém alterar a data de entrega de uma fase, você pode ir na aba **History** do item de trabalho e ver exatamente qual era a data anterior, quem alterou e quando. Isso funciona como uma "trilha de auditoria" da linha de base.

###### 2.8.5. Resumo: Como implementar agora?
Se você precisa de controle de linha de base hoje, o caminho mais rápido é:
1. Instalar uma extensão de **Gantt**.
2. Ou, se preferir não usar extensões, crie campos de **"Data Planejada"** e compare-os com as datas reais em um dashboard do Azure.
