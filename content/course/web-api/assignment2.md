---
title: Assignment Two
date: '2023-05-01'
type: book
weight: 30
---

## Purpose
The purpose of this assignment is to start working with Node.js and become more familiar with HTTP requests.

You will create a standard Node.js server to handle incoming HTTP requests and then respond with information about the request. The server should be able to read incoming header and query parameters and include this information in the response. The server should also only accept certain incoming requests and block others.

You may use any of the standard packages included in Node.js or any third-party packages to complete this assignment.

## Prerequisites

- Basic knowledge of JavaScript
- Basic knowledge of Node.js
- Node.js installed on your local machine
- Access to [GitHub Classroom](https://classroom.github.com/classrooms)
- Access to the [Base Repository](https://github.com/AliceNN-ucdenver/CSC3916_Assignment2)

## Step-by-step Guide

**1. Clone the Base Repository**

Clone the base repository located at [https://github.com/AliceNN-ucdenver/CSC3916_Assignment2](https://github.com/AliceNN-ucdenver/CSC3916_Assignment2) and create your own repository; GitHub classroom will do this when you accept the assigment

The scaffolding project contains the method to help you create the JSON object required for the HTTP response
```javascript
function getJSONObjectForMovieRequirement(req) {
    var json = {
        headers: "No headers",
        key: process.env.UNIQUE_KEY,
        body: "No body"
    };

    if (req.body != null) {
        json.body = req.body;
    }

    if (req.headers != null) {
        json.headers = req.headers;
    }

    return json;
}
```
**2. Create Environment Variable**

Create an environment variable UNIQUE_KEY and set it to a unique value.
- For local development, create a .env file (this file should be .gitignored and not stored in your repository).
- Create the environment variable on Heroku or Render for your app.

**3. Install Required Packages**

Ensure that you have installed all required packages such as `express`, `http`, `body-parser`, `passport`, `cors`, and `jsonwebtoken`.

**4. Create Routes for Signup and Signin**

Create two routes, `/signup` and `/signin`, to handle user registration and login.  The scaffolding project contains implementation of these methods for you

```javascript
router.post('/signup', (req, res) => {
    // Implementation here
});

router.post('/signin', (req, res) => {
    // Implementation here
});
```

**5. Update `/movies` Route**

Update the `/movies` route in your `server.js` to handle GET, POST, PUT, and DELETE requests.
- HTTP Method: GET should return `{ status: 200, message: ‘GET movies”, headers: headers: header from request, query: query string from request, env: your unique key }`
- HTTP Method: POST should return `{“status”: 200, message: “movie saved”, headers: headers: header from request, query: query string from request, env: your unique key }`
- HTTP Method: PUT should return `{“status: 200, message: “movie updated”, headers: headers: header from request, query: query string from request , env: your unique key }`
    - PUT should require authentication (JWT Auth)
- HTTP Method: DELETE should return `{“status: 200, message: “movie deleted”, headers: headers: header from request, query: query string from request, env: your unique key }`
    - Delete should require authentication (Basic Auth)

All other methods should return error (e.g. PATCH) - it should respond with a simple statement saying it doesn’t support the HTTP method.

```javascript
router.route('/movies')
    .get((req, res) => {
        // Implementation here
    })
    .post((req, res) => {
        // Implementation here
    })
    .put(authJwtController.isAuthenticated, (req, res) => {
        // HTTP PUT Method
        // Requires JWT authentication.
        // Returns a JSON object with status, message, headers, query, and env.
        var o = getJSONObjectForMovieRequirement(req);
        o.status = 200;
        o.message = "movie updated";
        res.json(o);
    })
    .delete(authController.isAuthenticated, (req, res) => {
        // HTTP DELETE Method
        // Requires Basic authentication.
        // Returns a JSON object with status, message, headers, query, and env.
        var o = getJSONObjectForMovieRequirement(req);
        o.status = 200;
        o.message = "movie deleted";
        res.json(o);
    })
    .all((req, res) => {
        // Any other HTTP Method
        // Returns a message stating that the HTTP method is unsupported.
        res.status(405).send({ message: 'HTTP method not supported.' });
    });
```

**6. Test Your Endpoints**

Test your endpoints with Postman. For each of the routes (GET, POST, PUT, DELETE), you should have tests that:

- Include valid requests, as well as requests that fail (e.g., missing authentication, sending an incorrect HTTP verb).
- Include tests with BasicAuth set to the correct username/password and sets with wrong password.
- Include tests that sign in and retrieve the JWT token that is then used to call the PUT method on /movies.

Here's a hint on how you can do this in Postman:

- For the sign-in test, create a request and store the token in the environment. Then use that token to call the PUT method on /movies.

```javascript
var data = JSON.parse(responseBody);
postman.setEnvironmentVariable("token", data.token);
```

**7. Share Your Postman Project**

Share your Postman project by creating a Postman Collection, running all the tests in the collection, and generating a public link to the collection.

**8. Create README.md and Submit the Assignment**

Create a `readme.md` at the root of your GitHub repository with the embedded link to your Postman collection. Submit the URL of your repository to the CSC_3916 assignment on Canvas.

---

Remember to make sure that your API is deployed to Heroku or Render and that your Postman tests are testing against this endpoint.

## Rubric

- -1 missing unique key 
- -1 basic auth not included
- -1 JWT auth missing
- -2 movies route issues (not responding with correct response)
- -2 missing postman requirements (-1 if just a minor miss)

## Resources
- [Node.js](http://nodejs.org)
- [Passport.js Documentation - Basic Digest](http://www.passportjs.org/docs/basic-digest/)
- [Render Documentation - Deploy Node.js & Express.js app](https://render.com/docs/deploy-node-express-app)

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/1e37a1a45fd828a9cb10)

