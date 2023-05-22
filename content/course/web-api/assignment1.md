---
title: Assignment One
date: '2023-05-01'
type: book
weight: 20
---

# Assignment One
## Purpose
The purpose of this assignment is to set up your GitHub and Render instances for future assignments. You will create an Echo server, setup auto-deployment on Render, and test the server using Postman.

## Prerequisites

1. Sign up for a free [GitHub](https://github.com/) account if you don't already have one.
2. GitHub Classroom will clone the repository [CSC3916_Assignment1](https://github.com/AliceNN-ucdenver/CSC3916_Assignment1) for you into your GitHub Classroom repository.
3. Sign up for a free account on [Render](https://render.com/).

## Steps

### Step 1: Creating an Echo Server

1. Navigate to the cloned repository on your GitHub Classroom repository.
2. Create a new file `server.js`.
3. Implement an Echo server using Node.js and Express.js. This server should respond with the same string it receives in a POST request.

### Step 2: Setting up Auto-deployment on Render

1. Follow the steps in the Render [guide](https://render.com/docs/deploy-node-express-app) to setup auto-deployment from your GitHub repository.

### Step 3: Creating a Postman Request

1. Open Postman and create a new POST request to your Render-deployed Echo server.
2. Create an environment variable `echo_body` for the body of your request.
3. In the 'Tests' tab, write tests to validate the response such as status code, response body, and response time.

    ```javascript
    // Check if the status code of the response is 200
    pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
    });

    // Check if the response time is less than 200ms
    pm.test("Response time is less than 200ms", function () {
        pm.expect(pm.response.responseTime).to.be.below(200);
    });

    // Check if the response body is equal to the echo_body environment variable
    pm.test("Response body is correct", function () {
        pm.expect(pm.response.text()).to.equal(pm.environment.get("echo_body"));
    });

    ```

### Step 4: Creating readme and Sharing Collection

1. Create a `readme.md` file at the root of your GitHub repository.
2. Share your Postman collection and include it in your readme. Make sure to include your environment settings.

### Step 5: Submission

1. Commit and push all your changes to your GitHub repository.
2. Submit the GitHub repository URL to Canvas.

## Rubric

- -5: Not deployed to Render.
- -5: Missing Postman Test.
- -1: For each missing assert (test).

## Resources

- [Node.js](http://nodejs.org)
- [Passport.js Documentation - Basic Digest](http://www.passportjs.org/docs/basic-digest/)
- [Render Documentation - Deploy Node.js & Express.js app](https://render.com/docs/deploy-node-express-app)
- [Creating an Echo Server in Node.js (YouTube Video)](https://www.youtube.com/watch?v=YUZGfjc9aLk)
- [How to write tests in Postman (YouTube Video)](https://www.youtube.com/watch?v=vhYD3G1QlEo)

Replace "your-collection-id" with the actual ID of your collection.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/your-collection-id)
