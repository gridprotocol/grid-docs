## /greet/cookie

This api is used by users to aquire the authorization to access the grid backend, including deploy app, access app.

The user address, timestamp and the signature of the timestamp is required when send this request.

## /greet/deployid

This api is used by users to deploy a selected app according to the id set in the request.

## /greet/show

This api is used by users to show the current status of app deployed on a provider. The cookie must be acquired before this api can work.

## /greet/clean

This api is used by users to clean all apps deployed on a provider, a cookie must be acquired beforehand.

## /greet/modellist

This api is used by users to show all supported models that can be deployed for now.
