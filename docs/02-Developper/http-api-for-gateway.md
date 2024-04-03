# /greet

greet API is used to check order infomation, verify payee and send a cookie when all check are passed.

## type=0

Do some basic check for a user's order.

## type=1

Verify the order's payee, and make this order available to this user when check is passed.

## type=2

After the identification with the signature and address, a cookie will be sent within the response for later access of some APIs like deploy and compute.

## type=3

This request type is used to deploy an application with a yaml file.