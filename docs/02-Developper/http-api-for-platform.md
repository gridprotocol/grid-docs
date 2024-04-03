# localhost:8081/registcp

registcp API used to register a cp(provider) into contract.
All infos about provider node and resource details must be set when request to this api.

# localhost:8081/listcp

listcp API list all provider node registered in the contract.

# localhost:8081/transfer

transfer API is called by a user with a token transfer tx hash. According to this definition, we can guess that a real token transfer operation must be taken before this user can call transfer API. This API works like a receipt recording operation, it just record the tx hash of the actual token transfer action, and the transfer record will be used to pay for credit(once for each transfer record).

# localhost:8081/listtransfer

listtransfer API just list all transfer record about a user. 

# localhost:8081/refreshtransfer

As we said before, a transfer records a token transfer operation and it's status. The confirmation status of the related tx hash must be true to make this transfer record available. The refreshtransfer API is used to acquire the latest confirmation status of this transfer tx.

# localhost:8081/pay

When a user has some transfer records(token transfered), he can use pay API to get some credit with a designated transfer record.
Call pay API with a transfer id to get credit for order purchasing.

# localhost:8081/listpay

List all pay history of a user.

# localhost:8081/querycredit

This API is used to query someone's credit balance with address.

# localhost:8081/createorder

This API is called by a user to create an order with a provider.
The provider address and number of each resource must be set in request, and the credit balance of this user must be enough to pay for this order.

# localhost:8081/listorder

This API is used to list all order details associated with an account.
