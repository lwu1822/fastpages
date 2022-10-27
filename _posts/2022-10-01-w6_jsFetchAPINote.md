---
toc: true
layout: post
description: Notes about Fetch API and an example 
categories: [js]
title: Fetch API Notes
comments: true
---

Below is a documentation of me learning about APIs. 

## What is an API? 
An API allows a developer to obtain data from web services. It performs abstraction to make tasks simpler for the user. Usually, an API acts between the application (what the user interacts with) and the server (contains the data, or **resource**). The process begins with the user creating an API call, which then proceeds with the application using the API to communicate with the server. The API then brings back the requested data to the user. 

## Types of APIs

### REST API 
The most common type of API is <mark>REST API</mark>. REST stands for Representational State Transfer. REST APIs are typically associated with JSON, although the payload (data that the API delivers), can be in the form of HTML or XML. REST is used because of its speed and reliability. It also allows services to be used through HTTP. 

Parts of a REST API include: 
* Endpoint: Includes URI: The url
* HTTP method: What the client wants to do with a resource
  Includes `GET` (get), `POST` (make), `PUT` (update), `DELETE` (remove)
* Headers: Contains things required for authentication and information about the client and server
* Body: Other info included in the request

When the client wants to access a resource, it sends a **HTTP Request** to the server. The server responds with a **HTTP Response** that contains data, or the **representation** about the resource, not the actual resource itself. The format of the representation cna be in XML or JSON. 

## What is Fetch API?
Fetch enables the user to make HTTP requests to servers. The Fetch API includes the `fetch()` method, which can take in two parameters, the URL and options. 

`fetch()` returns a `promise` that can be used with the `.then()` and `.catch()` methods as well as being able to use async/await.  

Once the request finishes, `promise` will resolve into a `Response` object.

`Response` is an <mark>API wrapper</mark> for what was fetched.

Now, what is an API wrapper?  

To understand this, a helpful website first explained what a wrapper is. Basically, a wrapper helps make an item simpler by "wrapping" over the item. For instance, it can use abstraction to help simplify code. It can also convert data to make it more compatible. 

Thus, an API wrapper allows you to combine many API calls into one to make things simpler. 

<br>

Alright, where was I? Right, `Response`. 

Feel like showing the response? Below is an example of reading the response if it is in raw text. (Don't really understand it at the moment, will research more about it later)

```
fetch('/readme.txt')
    .then(response => response.text())
    .then(data => console.log(data));
```

Question: Is `/readme.txt` the URL? It looks like a file... Can a file be a URL?

I'm guessing `/readme.txt` is the URL to the README file. 

Below is an explanation of a typical piece of code that you many find in a Fetch API: 
```
.then(response => response.json())
.then(data => console.log(data))
``` 

Question to self: What is the difference between `.then(data => console.log(data))` and `.then(response => console.log(response))`?

`response`: The response object that is returned by fetch.  

`response.json()`: The response object does not return directly accessible data. Instead, the response needs to parsed into JSON using the `json()` method. 

`data`: The JSON data 


<br>

You can also see the status code using the `Response` object. This can be accessed with the `status` property (`response.status`). 

Quick lesson on status codes:

* `200` is the status code you want, it means that the request was successful. 
* `404` means that what was requested does not exist
* `500` means that there is a server error

<mark>Note:</mark> `fetch` always succeeds, which means that even if the server responds with a 404, an error message would not show even if a `catch` statement was implemented. 



# Misc

Quick definition about entity: In programming, an entity is an object, which means it can include attributes and methods. 

Allows access to the API through a specific programming language.


<br>

Below is an example that uses the Fetch API to display airplane flight codes in a table:

<table>
  <thead>
  <tr>
    <th>IATA Code</th>
    <th>Name</th>
    <th>ICAO Code</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- generated rows -->
  </tbody>
</table>

<!--Script is layed out in a sequence (no function) and will execute when page is loaded-->
<script>


  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare fetch options
  const url = "https://iata-and-icao-codes.p.rapidapi.com/airlines";


const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'cc6d770f58msh120c53d95d27c68p1d2955jsn1898ff4fa031',
		'X-RapidAPI-Host': 'iata-and-icao-codes.p.rapidapi.com'
	}
};

fetch('https://iata-and-icao-codes.p.rapidapi.com/airlines', options)
	.then(response => response.json())
	.then(response => console.log(response))
	.catch(err => console.error(err));

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors
      if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
      }
      // valid response will have json data
      response.json().then(data => {
          console.log(data);

          

          // Country data
          for (const row of data) {
            console.log(row);

            // tr for each row
            const tr = document.createElement("tr");
            // td for each column
            const name = document.createElement("td");
            const cases = document.createElement("td");
            const deaths = document.createElement("td");
            const active = document.createElement("td");

            // data is specific to the API
            name.innerHTML = row.iata_code;
            cases.innerHTML = row.name; 
            deaths.innerHTML = row.icao_code; 

            // this build td's into tr
            tr.appendChild(name);
            tr.appendChild(cases);
            tr.appendChild(deaths);

            // add HTML to container
            resultContainer.appendChild(tr);
          }
      })
  })
  // catch fetch errors (ie ACCESS to server blocked)
  .catch(err => {
    console.error(err);
    const tr = document.createElement("tr");
    const td = document.createElement("td");
    td.innerHTML = err;
    tr.appendChild(td);
    resultContainer.appendChild(tr);
  });

</script>