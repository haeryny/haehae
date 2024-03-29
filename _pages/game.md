---
title: Dog Journal
layout: single
classes: wide
---
<html>

<html>
  <head>
    <title>Dog Journal</title>
    <style>
      html, body, input, textarea, select, button {  
      color: yellow !important;
      background-color: blue !important;
    }
      /* Add some basic styles */
      body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
      }

      h1 {
        text-align: center;
        font-size: 2rem;
        margin-top: 1rem;
      }

      section {
        margin-top: 2rem;
        padding: 1rem;
      }

      label {
        display: block;
        margin-top: 1rem;
      }

      input,
      textarea {
        padding: 0.5rem;
        margin-top: 0.5rem;
        width: 100%;
        box-sizing: border-box;
        border: 2px solid #ccc;
        border-radius: 5px;
        font-size: 1rem;
      }

      button {
        margin-top: 1rem;
        padding: 0.5rem;
        border: none;
        border-radius: 5px;
        background-color: #007bff;
        color: #fff;
        cursor: pointer;
        font-size: 1rem;
      }

      .description {
        font-style: italic;
        font-size: 0.8rem;
        margin-bottom: 0.5rem;
      }

      .journal-label {
        font-weight: bold;
        font-size: 1.2rem;
      }

      .entry-text-box {
        height: 10rem;
      }

      /* Add some responsive styles */
      @media screen and (min-width: 768px) {
        .container {
          max-width: 800px;
          margin: 0 auto;
        }

        section {
          padding: 2rem;
        }

        .entry-text-box {
          height: 15rem;
        }
      }
  </style>
  </head>


  <body> 
    <header>
      <!-- Pressing Submit will change the title of the journal to [insert name]'s Journal to make it more personal -->
      <h1 class="title" id="journal-name">My Dog's Journal</h1>
    </header>

  <!-- Create New Journal Entry Section -->
  <section class="section journal-section">
      <div class="container">
        <div class="container-row container-row-journal">
          <div class="container-item container-item-journal">
                
  <form id="entryForm" action="">

  <!-- Journal Entry Name -->
  <label for="entry-title" class="journal-label"></label>
                    <p class="description">Name Idea: Funny Event that happened today</p>
                    <input type="text" name="entry-title" id="entry-title" class="entry-text-title" placeholder="Name of entry "/>
                    
  <!-- Date -->
  <label for="entry-title" class="journal-label">Date</label>
                    <input type="text" name="entry-title" id="entry-title" class="date" placeholder="Date "/>

  <br><br>
                    
  <!-- Here's the main section of the journal, where the user writes about their dog's day for the journal -->
  <label for="entry" class="journal-label">Journal about your dog's day here...</label>
                    <textarea name="daily-entry" id="entry" class="entry-text-box" placeholder="What happened to your dog today?"></textarea>

  <!-- Here the user can enter three meals that their dog ate -->
  <label for="entry" class="journal-label">What did it eat today</label>
                    <p class="description">By putting down what they ate, you can track their diet. </p>
                    <textarea id="entry1" class="gratitude-text-box" placeholder="Breakfast"></textarea>
                    <textarea id="entry2" class="gratitude-text-box" placeholder="Lunch"></textarea>
                    <textarea id="entry3" class="gratitude-text-box" placeholder="Dinner"></textarea>

  <br><br>

  <!-- This is an API that generates a random dog fact -->
  <label for="entry" class="journal-label">Here are some dog facts!</label>
                     <button onclick="myFunction()">Click me</button>
    <p id="demo"></p>
    <script>
      function myFunction() {
        document.getElementById("demo").innerHTML = "Dogs can smell thousands of times better than humans. Their noses have millions more scent receptors.";
      }
    </script>

  <br><br><br>

  <br><br>
  <div>
  <!-- Submit button -->
  <button class="btn-main entry-submit-btn" type="submit">Submit</button>

  <!-- Here are all the journal entries that the user submitted -->
  <section class="section sectionEntryResults" id="entryResultsSection">
      <h2>Journal Entries</h2>
      <div class="container">
        <div class="container-row entryResultRow"></div>
      </div>
    </section>

  <script>
          /* eslint-disable */

      // Journal Entry Form
      // Here is getting all the variables and content from the journal entry form

      const entryForm = document.querySelector("#entryForm");
      const entryResultsSection = document.querySelector("#entryResultsSection");
      const entryResultRow = document.querySelector(".entryResultRow");

      const getEntryTitle = document.getElementsByClassName("entry-text-title");
      const getEntryText = document.getElementsByClassName("entry-text-box");
      const getEntryDate = document.getElementsByClassName("date");
      const getEntry1 = document.getElementById("entry1");
      const getEntry2 = document.getElementById("entry2");
      const getEntry3 = document.getElementById("entry3");
      const getEntryMeals = [getEntry1, getEntry2, getEntry3];


      // This adds the journal entry to the list
      function addEntryToDom(event) {
        event.preventDefault();

        const heading = document.createElement("h2");
        heading.className = "heading-results";
        entryResultRow.insertAdjacentElement("beforebegin", heading)

        // Adding Div
        const entryDiv = document.createElement("div");
        entryDiv.className = "single-entry-div";
        entryResultRow.appendChild(entryDiv);

        // Add entry title
        const entryHeading = document.createElement("h3");
        entryHeading.className = "single-entry-heading";
        entryHeading.textContent = getEntryTitle[0].value;
        entryDiv.appendChild(entryHeading);

        // Add entry date
        const entryDate = document.createElement("h4");
        entryDate.className = "single-entry-date";
        entryDate.textContent = getEntryDate[0].value;
        entryDiv.appendChild(entryDate);

        // Adding journal meal plans
        const entryMeals = document.createElement("p");
        entryMeals.className = "single-entry-date";
        entryMeals.textContent = "Meals: " + getEntryMeals[0].value + ", " + getEntryMeals[1].value + ", " + getEntryMeals[2].value;
        entryDiv.appendChild(entryMeals);

        // Adding journal body
        const entryParagraph = document.createElement("p");
        entryParagraph.className = "single-entry-text";
        entryParagraph.textContent = getEntryText[0].value;
        entryDiv.appendChild(entryParagraph);
        getEntryText[0].value = "";
        }
        

      // When the submit button is clicked, the addEntryToDom function will be executed
      entryForm.addEventListener("submit", addEntryToDom);

      // Dog Fact Generator
      function dogGen() {
          const options = {
	    method: 'GET',
	    headers: {
    		'X-RapidAPI-Key': '217acfa59emsh9a56b5c7ec9c672p11520bjsnbe23d137f1c8',
	    	'X-RapidAPI-Host': 'dogs6.p.rapidapi.com'
	    }
    };

    fetch('https://dogs6.p.rapidapi.com/facts', options)
	    .then(dogresponse => dogresponse.json())
	    .then(dogresponse => console.log(dogresponse))
	    .catch(err => console.error(err));
      }
  </script>

</div>

