# BetterProducts - Authentication

# Overview

The Authentication service is a crucial part of the BetterProducts application. It is the only part of the application
that is accessible to the public without any kind of prior authentication, being exposed by an Ingress. In this service
the user either creates a new account by signing up or logs in to an existing, after which he is provided a JWT that will
later be used for authentication and authorization. The service has to be available at all times, quick in processing 
user requests and generate secure JWTs.