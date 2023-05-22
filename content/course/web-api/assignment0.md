# Assignment Zero

## Purpose

In this assignment, you will familiarize yourself with **Postman**, **HTTP**, and **REST** protocols using the Postman testing framework. You will also create your first node program and commit it to GitHub. Your task will be to create a Postman collection and automate REST tests within the project. Each test should include the required assertions.

## Prerequisites

1. Create a free account on [GitHub](https://github.com/).
2. Accept GitHub Classroom – this should have been provided to you by your instructor.
3. Download an Integrated Development Environment (IDE). We recommend [WebStorm](https://www.jetbrains.com/webstorm/) or [VSCode](https://code.visualstudio.com/).
4. Download the desktop version of [Postman](https://www.postman.com/downloads/).

## Steps

### Step 1: Creating a REST Request

1. Open Postman.
2. Click on the 'New' button and select 'Request'.
3. Name your request (for instance 'Book Search') and select or create a new collection to store this request.
4. Set the request method to 'GET'.
5. Set the request URL to `https://www.googleapis.com/books/v1/volumes?q={{book_title}}`.
6. In the 'Tests' tab, add the asserts for the request validation.

### Step 2: Setting up the Environment Variable and Writing Tests

1. Click on the settings gear icon on the top right of Postman, then click 'Manage Environments'.
2. Click 'Add' to create a new environment. Name your environment (for instance 'Book Search Env').
3. Create a new variable named 'book_title' and set the initial value to 'Turing'.
4. In the Tests tab, write tests to validate the response. For instance:

    ```javascript
    pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
    });

    pm.test("Book title or description includes Turing", function () {
        var jsonData = pm.response.json();
        for (var i = 0; i < jsonData.items.length; i++) {
            if (/(turing)/i.test(jsonData.items[i].volumeInfo.title) || /(turing)/i.test(jsonData.items[i].volumeInfo.description)) {
                pm.environment.set("book_id", jsonData.items[i].id);
                break;
            }
        }
    });
    ```

### Step 3: Chaining Requests

1. Create a new request as in Step 1.
2. Set the request URL to `https://www.googleapis.com/books/v1/volumes/{{book_id}}`.
3. Similar to Step 2, write tests to validate the response.

### Step 4: Modifying googlebooks.js

1. Open your IDE and navigate to /utils/googlebooks.js.
2. Modify the method to return an object like:

    ```javascript
    {
        data: response.data, 
        status: response.status, 
        statusText: response.statusText, 
        headers: response.headers,
        requestHeader: response.config.headers
    }
    ```

### Step 5: HTTP Headers Analysis

1. Investigate the HTTP headers in the request and response from the Postman console.
2. Create a new text file named `headers.txt`.
3. Write a brief description of each key-value pair in the HTTP headers in the request and response.
4. Save the file and check it into your GitHub repository with the rest of the project.

## Submission

1. Create a readme.md file at the root of your GitHub repository.
2. Within your Postman collection, click on the arrow next to the collection name, then select 'Share'.
3. In the Share dialog, select 'Embed'.
4. Make sure to include your environment in the share by clicking 'Environment' and selecting the correct one.
5. Choose the 'Markdown' tab.
6. Click 'Copy to Clipboard' and paste this into your `readme.md` file.
7. Commit and push the updated `googlebooks.js` file to your GitHub repository.
8. Commit and push the `headers.txt` file containing your HTTP headers analysis to your GitHub repository.

## Rubric

- -10 points: homework not uploaded.
- -2 points: missing Postman button in readme.md.
- -2 points: missing check in request 1 for checking title and description in items.
- -2 points: missing ID check in request 2.
- -2 points: missing change in `utils/googlebooks.js` (adding new object).
- -2 points: missing text file with request headers.

## Resources

- [Creating a Test in Postman (YouTube Video)](https://www.youtube.com/watch?v=vhYD3G1QlEo)
- [Sharing a Live Version in Postman (YouTube Video)](https://www.youtube.com/watch?v=jmzp0oJ2O1U)
- [Postman Learning Center: Writing tests](https://learning.postman.com/docs/writing-scripts/test-scripts/)
- [Postman Learning Center: Sharing collections](https://learning.postman.com/docs/collaborating-in-postman/sharing/)

Replace "your-collection-id" with the actual ID of your collection.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/your-collection-id)

