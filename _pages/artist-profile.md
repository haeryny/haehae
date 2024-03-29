---
layout: single
title: Artists
---
<html>
<div id="demo">
  <p id="image" onmouseover="animateScript()" on.mouseout="stopAnimate()">

  </p>
</div>

<style>
#image {
  height: 256px;
  width: 256px;
  background: url('https://cdn.codeandweb.com/blog/2016/05/10/how-to-create-a-sprite-sheet/spritestrip.png') 0px 0px;
}
</style>

<script>
var tID; //we will use this variable to clear the setInterval()

function stopAnimate() {
  clearInterval(tID);
} //end of stopAnimate()


function animateScript() {

  var position = 256; //start position for the image slicer
  const interval = 100; //100 ms of interval for the setInterval()
  const diff = 256; //diff as a variable for position offset
  
  tID = setInterval(() => {
  
    document.getElementById("image").style.backgroundPosition =
      `-${position}px 0px`;
    //we use the ES6 template literal to insert the variable "position"
    
    if (position < 1536) {
      position = position + diff;
    }
    //we increment the position by 256 each time
    else {
      position = 256;
    }
    //reset the position to 256px, once position exceeds 1536px
    
  }, interval); //end of setInterval
} //end of animateScript()
</script>  
<html>


<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
* {
  box-sizing: border-box;
}

body {
  background-color: #82c5ff;
}

.row {
  display: flex;
}

.column {
  flex: 1;
  padding: 5px;
}


.card {
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
  background-color: #0357a1;
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

<html>
<head>
  <title>Artist Genre Searcher</title>
  <style>
    .container {
      max-width: 400px;
      margin: 0 auto;
      padding: 20px;
    }
    input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
    }
    button {
      padding: 10px 20px;
    }
    .artist-list {
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Artist Genre Finder</h1>
    <label for="genre-input">Enter the desired genre:</label>
    <input type="text" id="genre-input">
    <button onclick="sortArtists()">Find Artists</button>
    <div class="artist-list" id="artist-list"></div>
  </div>

  <script>
    // list of all the artists
    const artists = [
      { name: "Anitta", genre: "R&B/Soul" },
      { name: "Omar Apollo", genre: "Alternative/Indie" },
      { name: "DOMi & JD BECK", genre: "Jazz" },
      { name: "Muni Long", genre: "R&B/Soul" },
      { name: "Samara Joy", genre: "Jazz" },
      { name: "Latto", genre: "Hip-Hop/Rap" },
      { name: "Måneskin", genre: "Pop Rock" },
      { name: "Tobe Nwigwe", genre: "Hip-Hop/Rap" },
      { name: "Molly Tuttle", genre: "Folk" },
      { name: "Wet Leg", genre: "Alternative/Indie" },
      { name: "Mabu", genre: "Hip-Hop/Rap" },
      { name: "Alaina Castillo", genre: "Folk" },
      { name: "Dean", genre: "R&B/Soul" },
      { name: "Sean Yeung", genre: "Pop" },
      { name: "Amber Mark", genre: "R&B/Soul" },
    ];

    // function for sorting all the artists
    function sortArtists() {
      const desiredGenre = document.getElementById("genre-input").value.toLowerCase();
      const sortedArtists = artists.filter(artist => artist.genre.toLowerCase() === desiredGenre);
      sortedArtists.sort((a, b) => a.name.localeCompare(b.name));

      const artistList = document.getElementById("artist-list");
      artistList.innerHTML = "";

      if (sortedArtists.length > 0) {
        const listItems = sortedArtists.map(artist => `<li>${artist.name}</li>`);
        artistList.innerHTML = `<ul>${listItems.join("")}</ul>`;
      } else {
        artistList.innerHTML = "No artists found in the desired genre.";
      }
    }
  </script>
</body>
</html>

<div class="row">
  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Anitta</span>
          </div>
          <a href="https://en.wikipedia.org/wiki/Anitta_(singer)" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://images.hola.com/us/images/0277-159b34c4ab78-80f5ff3eee37-1000/horizontal-1200/anitta.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: R&B/Soul</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Omar Apollo</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://apeconcerts.com/wp-content/uploads/2019/07/omarapollo_19_1024-1.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Alt/Indie</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">DOMi & JD BECK</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://ichef.bbci.co.uk/news/976/cpsprodpb/13E87/production/_128534518_domiandjdpressphoto.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Jazz</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Muni Long</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://variety.com/wp-content/uploads/2022/01/MuniLong.jpg?w=1000" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: R&B/Soul</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Samara Joy</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://yt3.googleusercontent.com/QCROAE6X89edEDpIGvoGM9mDqX4kVwu2rpxCYOFbG8N9yVg6DvCZVOxbzqj57yRmwXQM-RjbRg=s900-c-k-c0x00ffffff-no-rj" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Jazz</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>
</div>

<div class="row">
  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Latto</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://i.insider.com/642bfb60fcb86b001803092b?width=700" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Hip-Hop/Rap</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Måneskin</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://www.nme.com/wp-content/uploads/2022/05/NME%E2%80%93MAneskin-EUROVISION%E2%80%93Credit-Fabio-Germinario-7_2000.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Pop Rock</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Tobe Nwigwe</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://www.okayafrica.com/media-library/image.jpg?id=18782629&width=1245&height=700&quality=85&coordinates=0%2C1358%2C0%2C1359" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Hip-Hop/Rap</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Molly Tuttle</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://www.paloaltoonline.com/news/photos/2019/september/25/80075_original.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Folk</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Wet Leg</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://media.npr.org/assets/img/2022/04/08/hollie-fernando_wet-leg-4-ret-240dpi-cca1fbaad9a5765d204b3d3cd169ff515e84a1dd-s1100-c50.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Alt/Indie</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>
</div>

<div class="row">
  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Mabu</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://i.ytimg.com/vi/SDLy2FagJEI/maxresdefault.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Hip-Hop/Rap</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Alaina Castillo</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://assets.teenvogue.com/photos/5e874b505bb5580009f27182/16:9/w_2560%2Cc_limit/Unknown.jpeg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Folk</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Dean</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://alchetron.com/cdn/dean-south-korean-singer-ef7fe26f-7391-49a8-92ce-fbd0163a4f9-resize-750.jpeg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: R&B/Soul</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Sean Yeung</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://github-production-user-asset-6210df.s3.amazonaws.com/111464920/240037244-28741ef6-018b-4e18-8e41-7da3823248fa.png" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: Pop</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="column">
    <div class="card">
      <section class="container content-section">
        <div class="shop-items">
          <div class="shop-item">
            <span class="shop-item-title">Amber Mark</span>
          </div>
          <a href="" class="card button">Learn More</a>
          <img class="shop-item-image" src="https://www.billboard.com/wp-content/uploads/2022/01/Billboard_Amber_Mark_006.jpg" alt="ARTIST" width="160" height="120">
          <div class="shop-item-details">
            <span class="shop-item-genre">Genre: R&B/Soul</span>
            <button class="btn btn-primary shop-item-button" type="button">ADD TO FAVORITES</button>
          </div>
        </div>
      </section>
    </div>
  </div>
</div>

<div class="column">
<section class="container content-section">
  <h2 class="section-header">Favorites</h2>
  <div class="cart-row">
  </div>
  <div class="cart-items">
  </div>

<script>
if (document.readyState == 'loading') {
    document.addEventListener('DOMContentLoaded', ready)
} else {
    ready()
}
// code for adding the artists to favorites
function ready() {
    var removeCartItemButtons = document.getElementsByClassName('btn-danger')
    for (var i = 0; i < removeCartItemButtons.length; i++) {
        var button = removeCartItemButtons[i]
        button.addEventListener('click', removeCartItem)
    }
    var quantityInputs = document.getElementsByClassName('cart-quantity-input')
    for (var i = 0; i < quantityInputs.length; i++) {
        var input = quantityInputs[i]
        input.addEventListener('change', quantityChanged)
    }
    var addToCartButtons = document.getElementsByClassName('shop-item-button')
    for (var i = 0; i < addToCartButtons.length; i++) {
        var button = addToCartButtons[i]
        button.addEventListener('click', addToCartClicked)
    }
}
// code to remove artist from favorites
function removeCartItem(event) {
    var buttonClicked = event.target
    buttonClicked.parentElement.parentElement.remove()
    updateCartTotal()
}
function addToCartClicked(event) {
    var button = event.target
    var shopItem = button.parentElement.parentElement
    var title = shopItem.getElementsByClassName('shop-item-title')[0].innerText
    var genre = shopItem.getElementsByClassName('shop-item-genre')[0].innerText
    var imageSrc = shopItem.getElementsByClassName('shop-item-image')[0].src
    addItemToCart(title, genre, imageSrc)
    updateCartTotal()
}
function addItemToCart(title, genre, imageSrc) {
    var cartRow = document.createElement('div')
    cartRow.classList.add('cart-row')
    var cartItems = document.getElementsByClassName('cart-items')[0]
    var cartItemNames = cartItems.getElementsByClassName('cart-item-title')
    for (var i = 0; i < cartItemNames.length; i++) {
        if (cartItemNames[i].innerText == title) {
            alert('This artist is already added to the favorites')
            return
        }
    }
    var cartRowContents = `
        <div class="cart-item cart-column">
            <img class="cart-item-image" src="${imageSrc}" width="100" height="100">
            <span class="cart-item-title">${title}</span>
        </div>
        <span class="cart-genre cart-column">${genre}</span>
        <div class="cart-quantity cart-column">
            <button class="btn btn-danger" type="button">REMOVE</button>
        </div>`
    cartRow.innerHTML = cartRowContents
    cartItems.append(cartRow)
    cartRow.getElementsByClassName('btn-danger')[0].addEventListener('click', removeCartItem)
    cartRow.getElementsByClassName('cart-quantity-input')[0].addEventListener('change', quantityChanged)
}
function updateCartTotal() {
    var cartItemContainer = document.getElementsByClassName('cart-items')[0]
    var cartRows = cartItemContainer.getElementsByClassName('cart-row')
    var total = 0
    for (var i = 0; i < cartRows.length; i++) {
        var cartRow = cartRows[i]
        var genreElement = cartRow.getElementsByClassName('cart-genre')[0]
        var quantityElement = cartRow.getElementsByClassName('cart-quantity-input')[0]
        var genre = parseFloat(genreElement.innerText.replace('$', ''))
        var quantity = quantityElement.value
        total = total + (genre * quantity)
    }
    total = Math.round(total * 100) / 100
    document.getElementsByClassName('cart-total-genre')[0].innerText = '$' + total
}
</script>