# Stacrypt

## Structure

```
.
|-- documentation
|   |-- stacrypt-api-doc
|   `-- stacrypt-meta
|
|-- utility
|   `-- bootstacrypt
|
|-- font-end
|   |-- stacrypt-web
|   |-- stacrypt-android *
|   `-- stacrypt-ios *
|
|-- services
|   |-- cryptodaemon
|   |-- stawallet
|   |-- stauth
|   `-- stamatcher
|
|
|-- stacrypt-web
|   |-- public
|   `-- src
|       |-- app
|       |-- auth
|       |-- index
|       |-- logo
|       `-- ticker
|-- stamatcher
|   |-- gradle
|   |   `-- wrapper
|   `-- src
|       `-- main
|           |-- kotlin
|           `-- resources
`-- stawallet
    |-- gradle
    |   `-- wrapper
    `-- src
        |-- main
        |   |-- java
        |   |-- kotlin
        |   |   `-- wallet
        |   `-- resources
        `-- test
            |-- java
            |-- kotlin
            `-- resources

```

## Services
#### Stawallet

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


#### Stabook


#### Stauth

## Components
#### stawallet-server
The main cryptocurrency wallet

###### Inputs:
* A synchronized daemon of each cryptocurrency

###### Cryptocurrency support:
* Bitcoin: bitcoind
* Litecoin: litecoind
* Ethereum: geth
* Ripple: rippled

#### stawallet-ui-admin
Web front-end of *stawallet-server*

