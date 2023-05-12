# API Gateway

The Ethereum developer community is recognized as the largest and most vibrant Blockchain ecosystem in the world today. There are a huge number of tools for DApp developers to engineer high quality smart contracts and application experiences, and you will find instructions on how to use many of those tools with Butane in our marketplace.


Even with all of these tools in place, and the straightforward nature of the Ethereum to DApp interface compared to other technologies in the Blockchain space, the amount of code and experience needed to connect application logic reliably with a Blockchain network can be significant.

 Thick libraries such as web3.js, web3j and Nethereum are often embedded inside the application to handle RLP encoding of transactions, and the complexities of the JSON/RPC native protocol of Ethereum. Wallet and key management,
 
  as well as signing and nonce management (which we discuss in detail later) must be handled in the application in a way that fits with the scaling characteristics.


In an Enterprise project, the Blockchain specialized DApp developers comfortable with these complexities are usually a small subset of the engineers that need to integrate and connect applications.

 Core system integration unique to each participant is required to allow projects to have meaningful impact on business processes, and data often needs to exchanged with the chain by various systems.


Many of these systems are sensitive to change, therefore Enterprise Application Integration tools and Enterprise Service Bus (ESB) architectures are used to integrate with them, rather than making direct changes to the applications themselves.


So in practice, the Blockchain interface used by participants to connect their systems to the ledger must be via standards based Web APIs and Messaging constructs that are consumable and reliable for multiple Enterprises in the business network. It is then extremely common to use this same layer to abstract the business application logic, such as Microservices forming a business application and user experience, from the blockchain via this same simple to consume API.


Butane provides this API Gateway layer out of the box. Using modern REST APIs with OpenAPI (Swagger) documentation, and backed by an infrastructure for Key management, signing, event steam management and high volume reliable transaction submission. 

The Gateway also supports direct Kafka connectivity for direct streaming of transactions from core systems and event-driven ESB technologies.