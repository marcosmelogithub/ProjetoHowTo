# Microsoft Office.js Guide

---

### Introdução

A plataforma de **Office Add-ins** (baseada em HTML, CSS e na **Office JavaScript API**) está disponível para uso efetivo há aproximadamente **13 anos**, considerando sua introdução inicial.

No entanto, a "disponibilidade efetiva" pode ser dividida em dois marcos principais, dependendo do que você considera uma tecnologia pronta para o mercado:

##### 1. O Surgimento (2012/2013)
A Microsoft introduziu o novo modelo de extensibilidade (na época chamado de "Apps for Office") com o lançamento do **Office 2013**.
* **O que mudou:** Foi o fim da dependência exclusiva de tecnologias legadas como VBA, COM e VSTO para criar suplementos.
* **Limitação:** Inicialmente, as APIs eram as chamadas **"Common APIs"**, que eram bastante limitadas e serviam apenas para interações básicas com o documento (como ler/escrever texto).

##### 2. A Maturidade e APIs Específicas (2015)
O uso tornou-se verdadeiramente robusto e comparável ao poder do VBA com o lançamento do **Office 2016**.
* **O que mudou:** A Microsoft lançou as **Application-Specific APIs** (como a `ExcelApi` e `WordApi`). Elas permitiram um controle muito mais profundo sobre os objetos nativos (formatação de células, criação de tabelas dinâmicas, parágrafos específicos, etc.).
* **Multiplataforma:** Foi a partir daqui que o conceito de "escreva uma vez, rode em qualquer lugar" (Web, Windows, Mac e iPad) se tornou a realidade prática que conhecemos hoje.

##### Resumo da Linha do Tempo

| Ano | Marco Principal | Status de Uso |
| :--- | :--- | :--- |
| **2012** | Lançamento da Office.js (v1.0) | Disponibilidade Inicial (Básica) |
| **2013** | Integração total no Office 2013 | Uso efetivo para suplementos de painel de tarefas |
| **2015** | Lançamento das APIs Específicas (v1.1+) | **Maturidade técnica** e expansão para Office 2016 |
| **2018+** | Introdução de Funções Personalizadas (Excel) | Substituição moderna para quase todas as funções VBA |


##### Conclusão
>Se você busca uma data de "uso profissional estável", a plataforma completou **10 anos de maturidade** em 2025/2026, embora tecnicamente exista desde o final de 2012. Hoje, ela é o padrão recomendado pela Microsoft, enquanto o VBA e o VSTO permanecem apenas em modo de manutenção para legado.

---

### Links

1. [Fundamentals of Building Office Add-ins with Office JavaScript APIs - John Brown](https://www.pluralsight.com/courses/build-office-addins-js-api)
>learn about communicating with external resources such as Trello, and about publishing the Add-in to the Microsoft Office Store. By the end of this course, you'll be ready to continue your learning for specific office applications like Excel and Word.
>
>[Curso online](https://app.pluralsight.com/ilx/video-courses/clips/289bef48-5e9d-4018-ab99-e7830ea53cce)


2. [Microsoft Learn - Documentação de Suplementos do Office](https://learn.microsoft.com/pt-br/office/dev/add-ins/)
>Utilize a plataforma Suplementos do Office para criar soluções que expandem aplicações do Office e interagem com conteúdos em documentos do Office e em mensagens de correio e itens de calendário do Outlook. Com os Suplementos do Office, pode utilizar tecnologias Web familiares, como HTML, CSS e JavaScript, para criar soluções que podem ser executadas em Office na Web, Windows, Mac e dispositivos móveis.

3. [Book - Building Office Add-ins using Office.js - Michael Zlatkovsky](https://leanpub.com/u/Zlatkovsky)
>

4. [Video - Start Learning Office Add-ins Development: Free Resources Guide - Andrew Connel](https://youtu.be/q-I4Oumy3bQ?si=cQWMDzJ1mM-4o_EA)
>00:00 : Introduction
>02:49 : Intro: Office Add-in Development
>13:33 : Office Add-ins - Fundamental components & different types
>17:35 : Fundamental Office Add-in extensibility components
>24:32 : Office JavaScript API
>26:16 : Office JS programming model
>33:07 : Development tools
>37:53 : Office Add-in capabilities
>38:06 : Microsoft Excel
>41:44 : Microsoft Outlook
>48:39 : Microsoft Word
>50:37 : Microsoft PowerPoint
>53:57 : Office Add-in customization
>01:04:51 : Testing, debugging, & deploying Office Add-ins
>01:14:44 : Adaptive Cards & Actionable messages
