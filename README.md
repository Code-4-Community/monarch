# 🦋 Monarch 🦋 

## ❤️ About the People

[Code4Community](https://c4cneu.com)'s newest project with [Lucy's Love Bus](https://lucyslovebus.org/).

Monarch is our internal code name for the prototype application we are developing to create a central hub for practitioners of integrative therapy. Our online search network will allow families across New England to discover which practitioners are in their area.

## 🛠 About the Tech

This project a monorepo with three major subdirectories. Navigate to each of them (linked below) for a more specific README.

The software system is composed of four major components:
1. [**frontend**](./frontend/README.md) : A web "frontend" client. The primary concern of this component is presentation code. This part of the system is built in React and Typescript, bundled as a single page application.
2. [**backend**](./backend/README.md) : A web "backend" server. The primary concern of this component is exposing a HTTP interface to the data and core business logic of the search network.
3. [**common**](./common/README.md) : Common units shared by and bundled with both of the above independent applications.
4. A database to securely store application data.


![Component Diagram](https://www.plantuml.com/plantuml/svg/NP1DIyD048Rl-ojUUceFZNUHqgIfA4Y9JS13yJ19Heacks5tWotYVtVCHv2UmimyypwJtJfFrdTDhLegFkcTiTZL5MkFo9elntQ1RmMSZao5Hvg4MDwyMQCzwtBr2dAu7olr0wMAsdGbmfTqs3gOaeCFX_svjUmSZliqGvWyIaWkkZaZ6eg_bVYYgJ5nX8D9dvyGawUS7FTO7FMIqyuqZT6GJsiqQ-yah-XxGzmmLsew3NU13JQJ1RTuoB8anPBFdgscUgN6aO2bW6AVcKfFZ1grwswzcVzQm4gki9vBv9V_oAIx8hRIakV-1G00)


## Development

1. Install Node v16.x

2. Start three terminal instances for each package in root:

``` sh
# /common
npm i
npm run watch # watches and incrementally compiles
```

``` sh
# /backend
npm i
npm start
```

``` sh
# /frontend
npm i
npm run dev
```

### Misc


``` plantuml
@startuml
package "Client Browser" {
  [React SPA (/frontend)] as Frontend
} 

cloud AWS {
  [Node.js Express REST API (/backend)] as Backend
  [DynamoDB NoSQL Database] as DB
} 

[Common Components (/common)] as Common

Frontend <.r.> Backend : HTTPS (external)
Backend <.d.> DB : HTTPS (internal)

Common -u-> Frontend : imported by
Common -u-> Backend : imported by
@enduml
```
