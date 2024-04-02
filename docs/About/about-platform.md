# Platform

The GRID platform provides interfaces for various common services to cater to different users. These services include computing node registration, order creation, token transfers, ERC20 deposits, and other functionalities.

## Provider Register/List

The purpose of registering their resource information in the contract is for computing nodes to make their resources known to user nodes. Only registered computing nodes can be discovered by user nodes and provide computing service for users.

## Order Creation

It is used for users to create service orders with selected nodes based on their resource requirements and pay the corresponding fees for the orders.

## Token Transfer

Users make actual payments using tokens through token transfers. Once the token transfer is successful, users can convert the tokens into credits by depositing them into their credits account. The credits are then used to pay for order fees.

## Credit Purchase

Users use token transfer records to recharge an equivalent amount of credits. These credits can be used to purchase orders. The cost of each order is calculated based on the quantity of ordered resources, the resource unit price provided by the node, and the duration of the order's service. The payment for the order is made using credits.

## Credit Query

Querying the current balance of a user's credit account.

## TX Confirmation

The transfer of token transactions (transfer) is an on-chain action, and the confirmation of transactions on the blockchain requires some time. The refresh interface is used to verify if the transfer transaction has been completed and to update the confirmation status of the transfer to true.
