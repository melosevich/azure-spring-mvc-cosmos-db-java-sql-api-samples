# Spring MVC with Azure Cosmos DB - sample
Sample e-commerce application built with Spring Boot (MVC on servlet stack) and "Spring Data Cosmos" client library for Azure Cosmos DB SQL API.

![Image](BookStore.png)

## Features

- @Query annotation for finder method
- Collection configuration with annotations(Indexing, RUs).
- Multiple database and collections accessed from single application.
- Auto generating UUID based IDs.
- Spring Data Repository pattern.
- Enabling cosmos request diagnostics
- Directly using CosmosAsynClient from a spring application.
- Infinite scroll with JQuery.

## Getting started

### Pre-requisites

- `Java Development Kit 8`. 
- An active Azure account. If you don't have one, you can sign up for a [free account](https://azure.microsoft.com/free/). Alternatively, you can use the [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) for development and testing. As emulator https certificate is self signed, you need to import its certificate to java trusted cert store, [explained here](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator-export-ssl-certificates).
- Maven.
- (Optional) SLF4J is a logging facade.
- (Optional) [SLF4J binding](http://www.slf4j.org/manual.html) is used to associate a specific logging framework with SLF4J.
- Clone the repo.

### Installation

1. Update the cosmos DB endpoint, key and locations information in application.properties
2. mvn spring-boot:run from the project base
3. On startup the application creates 2 databases and 4 collections between them.
4. Access the WebApp at http://localhost:81/ebooks/index
5. You will have to create user account to access the application functionality. The registration process asks for email ID, which will be used as the login ID. Any email address is fine as long as it has a valid format.
6. If you prefer docker:
    - mvn package
    - docker build -t <YOUR REPO>/ebookstorespringbootmvc .
    - docker run -p 80:80 -e azure.cosmos.bookstore.uri=<COSMOS_ENDPOINT> -e azure.cosmos.bookstore.key=<COSMOS_KEY> -t <YOUR REPO>/ebookstorespringbootmvc
    - Access the WebApp at http://localhost:81/ebooks/index