# Java Example implementation of a TMF 666 with MongoDB

## Description
To enable a fast implementation of new digital services, TMForum publishes the TMF Open API. Through these REST interface definitions, a standardized data exchange between telecommunication standard solutions and individually developed services is very easily possible.

This Github project shows how easy TMF Open APIs can be implemented using MongoDB as persistence layer. (Note: TMForum also provides reference implementations that can serve as a good basis for own TMF compatible services).

## Disclaimer
This service does not implement the complete TMF-666 specification and does not represent a finished project. 
## Details
The persistence was implemented exemplarily for `FinancialAccounts`, which is part of the [TMF666 Account Management API REST Specification](https://www.tmforum.org/resources/specification/tmf666-account-management-api-rest-specification-r19-0-0/). The `FinancialAccount` Resource is described starting on page 43 of the API Specification. The operations of `FinancialAccount` are described starting on page 83.

> An account of money owed by a party to another entity in exchange for goods or services that have been delivered or used. A financial (account receivable account/account payable) aggregates the amounts of one or more party accounts (billing or settlement) owned by a given party. It is a specialization of entity Account.

### Lifecycle
The Financial Account lifecycle is tracked by the `state` attribute.
Typical lifecycle values are: `Defined`, `Active`, `Suspended`, `pending Update`, `pending Closed`, `Closed`.
Note that an implementation of the specification may enrich the list of states depicted in the diagram.
The state machine specifying the typical state change transitions is provided below.

## How to use this Repo
First, update the `application.yml`. The only property that needs to be updated is `db.connectionString`.  
The Repo uses Maven to manage its dependencies. The project can be built with:
```shell
mvn clean install
```

Run the service (Sprint Boot) with:
```shell
mvn spring-boot:run
```

## Usage Samples
Here's an example of a request for creating a FinancialAccount resource. In this example the request only
passes mandatory attributes

### Create Financial Account
```JavaScript
POST http://localhost:8080/tmf-api/accountManagement/v4/financialAccount
Content-Type: application/json
{
 "name": "Administration account"
}
```
### Get Financial Accounts
```JavaScript
GET http://localhost:8080/tmf-api/accountManagement/v4/financialAccount
```

### Update a Financial Account
```JavaScript
PATCH http://localhost:8080/tmf-api/accountManagement/v4/financialAccount/{id}
```

## References

* [Blog Post - Why Telcos Implement TM Forum Open APIs with MongoDB](https://www.mongodb.com/blog/post/why-telcos-implement-tm-forum-open-apis-mongodb)
* [TMForum Open APIs](https://www.tmforum.org/open-apis)



