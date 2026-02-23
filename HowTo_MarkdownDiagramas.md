# markdowndiagramas
[Mermaid Page](https://mermaid.js.org/#/)
<br>
[Mermaid Sample Diagrams](https://mermaid.live/edit#pako:eNpVkT1PwzAQhv-KdRNIaRWn-Wg9INEUuhTBwETSwWqusdXGjhxHpST57zipEHCTT-_zvB6ug4MuEBgcz_pyENxY8r7JFXHzmKXCyMZWvNmT2eyh36IllVZ47cn6bqtJI3RdS1Xe3_j1CJG0240YEiukOg23KJ38V4U92WQ7Xltd7_8m7xfdk6dMvglX_z8RBp31nB05O_LZgRuScrMHD0ojC2DWtOhBhabi4wrdKOdgBVaYA3PPgptTDrkanFNz9aF19aMZ3ZYCXO-5cVtbF9ziRvLS8F8EVYEm1a2ywAKaTB3AOvgEtoiDOaXhivqULpfxYhF5cAUWruZRHIRJGMZJHK0COnjwNf3qz5dJ5LsJYj9J_MDxWEirzcvtBtMphm85xHsb)

---
##### Tabela com os tipos de setas de direcionamento suportados atualmente

| *Type* | *Description* |
| :---: | :---|
| -> | Solid line without arrow |
| --> | Dotted line without arrow |
| ->> | Solid line with arrowhead |
| -->> | Dotted line with arrowhead |
| -x | Solid line with a cross at the end |
| --x | Dotted line with a cross at the end |
| -) | Solid line with an open arrow at the ende (async) |
| --) | Dotted line with a open arrow at the ende (async) |

---
##### Flowchart
```mermaid
flowchart TD
    A[Christmas] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[Car]
```

---
##### TimeLine
```mermaid
timeline
    title History of Social Media Platform
    2002 : LinkedIn
    2004 : Facebook
         : Google
    2005 : YouTube
    2006 : Twitter
```
---
##### Class
```mermaid
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
      +String beakColor
      +swim()
      +quack()
    }
    class Fish{
      -int sizeInFeet
      -canEat()
    }
    class Zebra{
      +bool is_wild
      +run()
    }
```

---
##### Sequence
```mermaid
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```

---
##### Diagrama com decisão
```mermaid
flowchart LR
A(["Start"])
A --> B{"Decision"}
B --> C["Option A"]
B --> D["Option B"]
```

---
##### ExR
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : includes
    CUSTOMER {
        string id
        string name
        string email
    }
    ORDER {
        string id
        date orderDate
        string status
    }
    PRODUCT {
        string id
        string name
        float price
    }
    ORDER_ITEM {
        int quantity
        float price
    }
```

---
##### MindMap
```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectiveness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

---
##### Architecture
```mermaid
architecture-beta
    group api(cloud)[API]

    service db(database)[Database] in api
    service disk1(disk)[Storage] in api
    service disk2(disk)[Storage] in api
    service server(server)[Server] in api

    db:L -- R:server
    disk1:T -- B:server
    disk2:T -- B:db
```

