# BetterProducts - Backend

## Overview

This is an overview of the entire backend of the BetterProducts application. It includes the entirety of a user's
task flow. For this we will take multiple instances of how something that a user wants to do is completed inside the 
backend. The completion of these tasks is dependent on many different service that all work together to process user
requests and deliver an appropriate response. The BetterProducts backend contains these services:
- ApiGateway service
- Customer service
- Key service
- Order service
- Sale service
- Storage service
- Review service
Other services that will be added after are:
- Notification service
- Payment service
- Recommendations service
- Tracing service

## Sale Process

When a user/customer wants to put an item for sale there are many different actions that must be completed by the service
to ensure that the item is put for sale:
1. The user interacts with the frontend  and completes the form for putting an item for sale.
2. The request is then forwarded to an instance of the ApiGateway in the private backend network through an Ingress.
3. The request is authenticated through JWT and CSRF token authentication and then routed to an instance of the Sale service
4. The Sale service contacts the Storage service to add an item to the storage as it was just put for sale.                 
5. After the item is added to the storage a notification is sent asynchronously to the user through their email to inform
them they put the item on sale.
With this all the work of the backend to put an item on sale is done.

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="/Backend/Images/SaleDark.png">
    <source media="(prefers-color-scheme: light)" srcset="/Backend/Images/SaleLight.png">
    <img alt="Log-in Explanation" src="/Backend/Images/SaleLight.png">
</picture>