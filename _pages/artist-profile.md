---
layout: single
title: Artists
---
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
* {
  box-sizing: border-box;
}

.row {
  display: flex;
}

.column {
  flex: 1;
  padding: 5px;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  max-width: 200px;
  margin: auto;
  text-align: center;
  font-family: arial;
  justify-content: center;
  align-items: center;
}

.price {
  color: grey;
  font-size: 22px;
}

.card button {
  border: none;
  outline: 0;
  padding: 12px;
  color: white;
  background-color: #006400;
  text-align: center;
  cursor: pointer;
  width: 80%;
  font-size: 18px;
}

.card button:hover {
  opacity: 0.7;
}
</style>
</head>
<body>

<h1>Looking for new people to listen to? Need better music taste? Go here!</h1>
<h3>Searching algorithm to search for artists here</h3>

<div class="row">
  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Artist Name</span>
          </div>
          <a href="https://haeryny.github.io/teamteam/doginfo/" class="card button">Learn More</a>
          <img class="shop-item-image" src="" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-price">Genre: Artist Genre</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>
</div>