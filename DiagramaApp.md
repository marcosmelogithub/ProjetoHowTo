# Diagrama da Aplicação HowTo

## 1. Fluxo Geral da Aplicação

```mermaid
flowchart TD
    A[Página Carrega] -->|DOMContentLoaded| B[initializePage]
    B --> C[listMarkdownFiles]
    C --> D{Requisição<br/>GitHub API}
    D -->|Sucesso| E[Filtrar Arquivos .md<br/>iniciados com HowTo]
    D -->|Erro| F[Mostrar Erro]
    E --> G[Obter Primeira Linha<br/>de cada arquivo]
    G --> H[Construir Lista HTML<br/>com Links]
    H --> I[Exibir Lista<br/>na Página]
    I --> J{Usuário Clica<br/>em um Arquivo}
    J -->|Sim| K[displayMarkdownContent]
    K --> L[Buscar Conteúdo<br/>Completo do Arquivo]
    L --> M[Renderizar Markdown<br/>com marked.js]
    M --> N[Converter URLs<br/>de Imagens]
    N --> O[Renderizar<br/>Diagramas Mermaid]
    O --> P[Exibir Conteúdo<br/>Formatado]
    J -->|Não| J
    F --> Q[Fim]
    P --> Q
```

## 2. Arquitetura de Componentes

```mermaid
graph LR
    A[index.html] -->|Carrega| B[functions.js]
    A -->|Importa| C[marked.js<br/>CDN]
    A -->|Importa| D[mermaid.js<br/>CDN]
    B -->|Usa API| E[GitHub API<br/>Repositório]
    E -->|Retorna| F[Arquivo .md<br/>Conteúdo]
    C -->|Renderiza| F
    D -->|Renderiza| G[Diagramas<br/>Mermaid]
    F --> H[Conteúdo HTML]
    G --> H
    H -->|Exibe| I[Navegador]
```

## 3. Fluxo de Carregamento de Arquivos

```mermaid
sequenceDiagram
    participant User as Usuário
    participant Browser as Navegador
    participant JS as functions.js
    participant API as GitHub API
    participant Raw as GitHub Raw

    User->>Browser: Acessa index.html
    Browser->>JS: Executa script
    JS->>API: GET /repos/.../contents/
    API-->>JS: Lista de arquivos
    JS->>JS: Filtra .md com HowTo
    loop Para cada arquivo
        JS->>Raw: GET conteúdo (primeira linha)
        Raw-->>JS: Primeira linha
    end
    JS-->>Browser: HTML com lista de links
    Browser-->>User: Exibe lista
    User->>Browser: Clica em um arquivo
    Browser->>JS: onclick displayMarkdownContent
    JS->>Raw: GET conteúdo completo
    Raw-->>JS: Arquivo markdown
    JS->>JS: marked.parse()
    JS->>JS: Processa imagens
    JS->>JS: Processa mermaid
    JS-->>Browser: HTML renderizado
    Browser-->>User: Exibe conteúdo
```

## 4. Estrutura de Dados - Arquivo Markdown

```mermaid
graph TB
    A[Arquivo .md<br/>GitHub] --> B{Conteúdo}
    B --> C[Metadados]
    B --> D[Texto Markdown]
    B --> E[Links Relativos<br/>para Imagens]
    B --> F[Blocos Mermaid]
    C --> G[Primeira Linha<br/>extração]
    D --> H[marked.parse<br/>conversão]
    E --> I[Conversão para URL<br/>arquivo absoluta GitHub]
    F --> J[Substituição<br/>em div.mermaid]
    G --> K[Renderização<br/>Final]
    H --> K
    I --> K
    J --> K
    K --> L[Página Exibida]
```

## 5. Estrutura das Funções Principais

```mermaid
graph TB
    A[initializePage] --> B[listMarkdownFiles]
    B --> C[getFirstLine]
    B --> D[Contruir HTML<br/>com Links]
    D --> E[onclick<br/>displayMarkdownContent]
    E --> F[fetch<br/>GitHub Raw]
    F --> G[marked.parse]
    G --> H[Processar<br/>Imagens]
    H --> I[Processar<br/>Mermaid]
    I --> J[mermaid.contentLoaded]
    J --> K[Exibir<br/>Conteúdo]
    C --> L[fetch<br/>GitHub Raw]
    L --> M[Extrair<br/>primeira linha]
    M --> N[Retornar<br/>Título]
```

## 6. Mapa de Eventos

```mermaid
graph LR
    A[DOMContentLoaded] -->|dispara| B[initializePage]
    B --> C[listMarkdownFiles]
    C --> D{Requisição API}
    D -->|sucesso| E[renderizar lista]
    D -->|erro| F[mostrar erro]
    G[onclick em link] -->|dispara| H[displayMarkdownContent]
    H --> I[renderizar conteúdo]
```

## 7. Fluxo de Tratamento de Erros

```mermaid
graph TD
    A[Operação] --> B{Resposta OK?}
    B -->|Não| C[Capturar Erro]
    B -->|Sim| D[Processar Dados]
    C --> E[console.error]
    C --> F[Mostrar Mensagem<br/>de Erro ao Usuário]
    E --> G[Fim]
    D --> H{Processamento<br/>OK?}
    H -->|Sim| I[Exibir Resultado]
    H -->|Não| C
    I --> G
    F --> G
```

## 8. Dependências Externas

```mermaid
graph TB
    A[index.html] --> B["marked@latest<br/>CDN jsdelivr"]
    A --> C["mermaid@latest<br/>CDN jsdelivr"]
    A --> D[functions.js]
    
    B --> E["Converte Markdown<br/>em HTML"]
    C --> F["Renderiza Diagramas<br/>Mermaid"]
    D --> G["GitHub API<br/>repos/contents"]
    D --> H["GitHub Raw<br/>raw.githubusercontent.com"]
    
    E --> I[Renderização<br/>Final]
    F --> I
    G --> J[Lista de<br/>Arquivos]
    H --> K[Conteúdo<br/>dos Arquivos]
    J --> I
    K --> I
```

## 9. Configurações e Constantes

```mermaid
graph LR
    A["Constantes em functions.js"]
    A --> B["GITHUB_REPO_URL<br/>api.github.com/.../"]
    A --> C["GITHUB_RAW_URL<br/>raw.githubusercontent.com/..."]
    B --> D["Listar Arquivos<br/>da API"]
    C --> E["Buscar Conteúdo<br/>dos Arquivos"]
    D --> F["listMarkdownFiles"]
    E --> G["getFirstLine &<br/>displayMarkdownContent"]
    F --> H["Aplicação"]
    G --> H
```

## Resumo da Lógica

A aplicação funciona como um **navegador web de arquivos markdown** hospedados no GitHub:

1. **Inicialização**: Quando a página carrega, invoca `initializePage()` que chama `listMarkdownFiles()`
2. **Listagem**: Consulta a API do GitHub para obter a lista de arquivos `.md` que começam com "HowTo"
3. **Títulos**: Para cada arquivo, extrai a primeira linha como título usando `getFirstLine()`
4. **Interface**: Cria uma lista HTML com links clicáveis para cada arquivo
5. **Visualização**: Quando o usuário clica em um arquivo:
   - Busca o conteúdo completo via GitHub Raw URL
   - Renderiza o markdown usando a biblioteca `marked.js`
   - Converte URLs relativas de imagens em URLs absolutas do GitHub
   - Processa blocos de código `mermaid` como diagramas
   - Renderiza os diagramas usando `mermaid.js`

**Fluxo de Dados**: GitHub → API/Raw URLs → HTML → Browser → Usuário

**Tecnologias**: Vanilla JavaScript, Marked.js, Mermaid.js, GitHub API
