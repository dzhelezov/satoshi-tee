# satoshi-tee
A TEE based tool for distributing shares of Satoshi's treasure in a trustless way



Here is a rough idea how one can safely redistribute rewards among hunters. Each member has a payout address. The team decides on who gets what based on the contribution (the team should reach consensus about the shares beforehand). Upon agreement, the team prepares a btc transaction with the treasure as a single input and with an outputs for each team member. Then the team sets up a secure TEE (trusted execution environment), aws and azure seem to support that. The enclave should be able to generate a private key no one can retrieve (even admins). Then each member can encrypt it’s share with the enclave key and submit its share. The enclave code decrypts the share, calculates the key and (assuming the key opens the tx lock) submits the transaction to the bitcoin network.

To environment can support different teams by keeping different transactions. In this case, a share request should contain a transaction hash in order to indicate which team the share belongs to. 

## Cloud-based confidential computing

It seems that currently only Microsoft Azure [provides](https://azure.microsoft.com/en-us/solutions/confidential-compute/) TEE as a service on the Cloud. Microsoft also provides [Open Enclave SDK](https://github.com/Microsoft/openenclave) for TEE-enabled apps.
