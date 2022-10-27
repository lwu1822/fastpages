---
toc: true
layout: post
description: it finally worked ;-;
categories: [API]
title: JavaScript Fetch API
comments: true
---

Below is a table created using HTML. The table displays the word bright, and its definition, which was taken from an API. The API was called using JavaScript Fetch. 

<table>
  <thead>
  <tr>
    <th>Word</th>
    <th>Definition</th>
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
  const url = "https://dictionary-by-api-ninjas.p.rapidapi.com/v1/dictionary?word=bright";


const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'cc6d770f58msh120c53d95d27c68p1d2955jsn1898ff4fa031',
		'X-RapidAPI-Host': 'dictionary-by-api-ninjas.p.rapidapi.com'
	}
};

fetch('https://dictionary-by-api-ninjas.p.rapidapi.com/v1/dictionary?word=bright', options)
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
      response.json().then(response => {
      
            console.log(response);

          

          // Country data
         
            console.log(response.word);

            // tr for each row
          const tr = document.createElement("tr");
            // td for each column
          const word = document.createElement("td");
          const definition = document.createElement("td");
            

            // data is specific to the API
            word.innerHTML = response.word;
            definition.innerHTML = response.definition;

            // cases.innerHTML = row.name; 
           //  deaths.innerHTML = row.icao_code; 

            // this build td's into tr
            tr.appendChild(word);
            tr.appendChild(definition);
           // tr.appendChild(cases);
          //  tr.appendChild(deaths);

            // add HTML to container
            resultContainer.appendChild(tr);
          
        
          
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