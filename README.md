# Stacrypt

Stacrypt is a multi-cryptocurrency exchange.

## Directory Structure

```
stacrypt
|-- documentation
|   |-- stacrypt-api-doc
|   `-- stacrypt-meta
|
|-- utility
|   |-- cryptodaemon
|   `-- bootstacrypt
|
|-- font-end
|   |-- stacrypt-web
|   |-- stacrypt-android (TODO)
|   `-- stacrypt-ios (TODO)
|
|-- services
|   |-- stawallet
|   |-- stemerald
|   |-- stexchange
|   |-- stauth (DEPRECATED)
|   `-- stamatcher (DEPRECATED)
|
|-- add-on services
|   |-- stariskless (TODO)
|   `-- stamaker (TODO)
|
|-- common
|   `-- stapi-common (DEPRECATED)
|
`-- admin
    `-- stawallet-web (TODO)

```

| Repositories |
|---|
| [stacrypt-api-doc](https://github.com/mahdi13/stacrypt-api-doc) |
| [stacrypt-meta](https://github.com/mahdi13/stacrypt-meta) |
| [cryptodaemon](https://github.com/mahdi13/cryptodaemon) |
| [bootstacrypt](https://github.com/mahdi13/bootstacrypt) |
| [stacrypt-web](https://github.com/mahdi13/stacrypt-web) |
| [stawallet](https://github.com/mahdi13/stawallet) |
| [stemerald](https://github.com/mahdi13/stemerald) |
| [stexchange](https://github.com/mahdi13/stexchange) |


## Technology Stack

Architecture:

| Technology | Development | Deployment |
|---|---|---|
| OS | Ubuntu | Alpine + Ubuntu |
| Container | (Docker) | Docker |
| Cluster | (Docker Compose) | Kubernate |
| Secret Manager | Vault | Vault |
| Service Discovery | Consul | Consul |
| Broker | ZooKeeper | ZooKeeper |


Backend:

| Technology | StaWallet | StExchange | StEmerald |
|---|---|---|---|
| Language | Kotlin | C | Python |
| Framework | Ktor | network | Restfulpy |
| API | Json-RPC + REST | Json-RPC + Websocket | REST |
| Streaming | - | Kafka | - |
| Database | Xodus | MySQL + REDIS | REDIS |
| Database Migration | - | - | Alembic |


Frontend:

| Technology | Web | Android | iOS |
|---|---|---|---|
| Language | Kotlin | KotlinJS | KotlinNative + Swift |
| Framework | React | Anko | - |
| Interface | Material | Material | Material |
| Build System | Webpack | Gradle | - |


## Services
#### Stawallet
The main cryptocurrency wallet

###### RPC API
* createPayment(): {address: String, data: String}
Return an address and maybe a data to receive new cryptocurrency transaction.
Usage is different per cryptocurrency. For example:
    * `Bitcoin`: Return a new address (without any data)
    * `Ethereum`: Return a new address (without any data)
    * `Ripple`: Return a static address and a new `invoice_id`

###### Rest API (Admin)
* `/wallets/{cryptocurrency_code}` GET
Returns the complete information about each wallet

* `/wallets/{cryptocurrency_code}/transactions` GET
* `/wallets/{cryptocurrency_code}/addresses` GET



## Components
#### stawallet
The main cryptocurrency wallet

###### Inputs:
* A synchronized daemon of each cryptocurrency

###### Cryptocurrency support:
* Bitcoin: bitcoind
* Litecoin: litecoind
* Ethereum: geth
* Ripple: rippled

#### stawallet-web
Web front-end of *stawallet-server*
