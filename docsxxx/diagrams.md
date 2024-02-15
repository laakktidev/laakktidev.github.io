


Muuten ok mutta response clientille kun storen jälkeen haetaan uudelleen mongosta
Tosin jos geometrille ei ole kuvia response list ei toimi

```mermaid
sequenceDiagram
    autonumber
    participant Client
    participant Server
    participant MongoDB
    participant SentinelHub

    Client->>Server: Request
    Server->>MongoDB: Query
    MongoDB-->>Server: Data
    alt Data found in MongoDB
        Server-->>Client: Response
    else Data not found in MongoDB
        Server->>SentinelHub: Request
        SentinelHub-->>Server: Response
        Server->>MongoDB: Store Data
        Server-->>Client: Response
    end
```

Participants:

Client: The entity initiating the request.
Server: The central processing entity that handles client requests, communicates with MongoDB, and interacts with SentinelHub.
MongoDB: The database used to store and retrieve data.
SentinelHub: An external service from which the server can request data.
Sequence of Interactions:

The "Client" sends a "Request" to the "Server."
The "Server" checks if the required data is available in "MongoDB" by sending a "Query" to it.
If the data is found in "MongoDB," it responds directly to the "Client" with a "Response."
If the data is not found in "MongoDB" after receiving a response from "SentinelHub," the "Server" stores the data in "MongoDB."
The "Server" then retrieves the data from "MongoDB."
Finally, the "Server" responds to the "Client" with the retrieved data.

```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant MongoDB
    participant SentinelHub

    Client->>Server: Request
    Server->>MongoDB: Query
    MongoDB-->>Server: Data
    alt Data found in MongoDB
        Server-->>Client: Response
    else Data not found in MongoDB
        Server->>SentinelHub: Request
        SentinelHub-->>Server: Response
        Server->>MongoDB: Store Data
        Server->>MongoDB: Retrieve Data
        MongoDB-->>Server: Retrieved Data
        Server-->>Client: Response
    end
```



```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant MongoDB
    participant SentinelHub

    Client->>Server: Request
    Server->>MongoDB: Query
    MongoDB-->>Server: Data
    alt Data found in MongoDB
        Server-->>Client: Response
    else Data not found in MongoDB
        Server->>SentinelHub: Request
        SentinelHub-->>Server: Response
        Server->>MongoDB: Store Data
        Server->>MongoDB: Query
        MongoDB-->>Server: Data
        Server-->>Client: Response
    end
```
:::

```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant MongoDB
    participant SentinelHubXX

    Client->>Server: Request
    Server->>MongoDB: Query
    MongoDB-->>Server: Data

    alt Data found in MongoDB
        Server-->>Client: Response (Data found in MongoDB)
        Note right of Server: Data found in MongoDB
    else Data not found in MongoDB
        Server->>SentinelHubXX: Request
        SentinelHubXX-->>Server: Response (Data not found in MongoDB)
        Server->>MongoDB: Store Data
        Server->>MongoDB: Query
        MongoDB-->>Server: Data
        Server-->>Client: Response (Data not found in MongoDB)
        Note right of Server: Data not found in MongoDB
    end
```
:::


```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#BB2528',

 graph LR;
 A[Wiki supports Mermaid] --> B[Visit https://mermaidjs.github.io/ for Mermaid syntax];


      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
        graph TD
          A[Christmas] -->|Get money| B(Go shopping)
          B --> C{Let me think}
          B --> G[/Another/]
          C ==>|One| D[Laptop]
          C -->|Two| E[iPhone]
          C -->|Three| F[fa:fa-car Car]
          subgraph section
            C
            D
            E
            F
            G
          end
```
:::

```mermaid
flowchart TB

subgraph personalBankingCustomer[Personal Banking Customer]
    h1[-Person-]:::type
    d1[A customer of the bank, with \n personal bank accounts]:::description
end
personalBankingCustomer:::person

subgraph internetBankingSystem[Internet Banking System]
    h2[-Software System-]:::type
    d2[Allows customers to view \n information about their bank \n banks, and make payments]:::description
end
internetBankingSystem:::internalSystem

subgraph mainframeBankingSystem[Mainfram Banking System]
    h3[-Software System-]:::type
    d3[Stores all of the core banking \n information about customers, \n accounts, transactions etc]:::description
end
mainframeBankingSystem:::externalSystem

subgraph emailSystem[Email System]
    h4[-Software System-]:::type
    d4[The internal Microsoft Exchange \n email system]:::description
end
emailSystem:::externalSystem

personalBankingCustomer--Views account \n balances, and \n makes payments \n using-->internetBankingSystem
internetBankingSystem--Gets accounts \n information from, \n and makes \n payments using-->mainframeBankingSystem
internetBankingSystem--Sends emails using--> emailSystem
emailSystem--Sends emails to-->personalBankingCustomer

%% Element type definitions

classDef person fill:#08427b
classDef internalSystem fill:#1168bd
classDef externalSystem fill:#999999

classDef type stroke-width:0px, color:#fff, fill:transparent, font-size:12px
classDef description stroke-width:0px, color:#fff, fill:transparent, font-size:13px
```
:::

```mermaid
graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
C -->|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| F[fa:fa-car Car]

classDef node fill:#0f0,stroke-width:4px;
classDef red fill:#f00,stroke-width:1px;
class B red;
```

```mermaid
graph LR
MyApp --> DB(fa:fa-database MySQL)

style DB fill:#00BBFF
```