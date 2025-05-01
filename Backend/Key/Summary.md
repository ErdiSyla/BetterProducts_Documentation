# BetterProducts - Key

# Overview

The Key service is a crucial part of the BetterProducts application. It generates and manages TokenKeys, an object which carries 
a RSA KeyPair. These keys are then use to sign and validate JWTs which are used for authentication throughout the
application. The service sends these keys to all other services that need them through Kafka. The TokenKeys are saved in 
the TokenKeyRepository and after a specific amount of time are then marked as "GRACE" keys, because they are only to be 
used for validating existing keys and not signing any new keys. The next time the service starts validating key expiry 
all "GRACE" keys are deleted.