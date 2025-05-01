# BetterProducts - Log in

# Overview

This is a detailed explanation about how a user would log in to the BetterProducts application. It explains the entire
roadmap taken from the request until the response step by step. For any change to the workflow of logging in, this file 
will also be changed to present the most up-to-date version of the process.

# Detailed Explanation

After a request with all the necessary information is made from the frontend using the url 
https://betterproductivity/auth/login.com, the user sends the necessary information to AuthController. The information has to
contain the user's email and password as a JSON formatted string. The credentials are then sent to the AuthenticationService
class where further processing is done. In the AuthenticationService class, the first thing checked is if a user with the
same email exists inside our databases. If no user with a matching email is found then a NoUserExistsException is thrown.
If a user is found then the password provided by the user and the one inside our databases are checked if they match. If
they do not match an InvalidLogInException is thrown, if they do then the request proceeds to the JWT generation. Here a
JWT is created inside the JWTService class. In the JWTService class, using an RSA private key the JWT is signed and 
given an expiration date of 2 weeks. After that it is added to a cookie by a method call made by AuthenticationService to
JWTService, finally a ResponseEntity is returned to the AuthController class with a HTTPStatus of 200/OK and body with 
the content "Login successful.".

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="../Images/SignInDark.png">
    <source media="(prefers-color-scheme: light)" srcset="../Images/SignInLight.png">
    <img alt="Log-in Explanation" src="../Images/SignInLight.png">
</picture>