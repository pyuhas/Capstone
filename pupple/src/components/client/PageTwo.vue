//All html goes here
<template lang="html">
  <div class="PageTwo">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>New buddy:</title>
      <link rel="stylesheet" href="styles.css">
      <link rel="stylesheet" type="text/css" href="//fonts.googleapis.com/css?family=Comfortaa" />
    </head>

    <body>
      <header class="site-header">
        <h1 class="site-header-1">Here is your new buddy:</h1>
        <nav class="site-nav--main">
        <form class="button">
          <input type="button" value="Go Back" onclick="history.go(-1)">
        </form>
        </nav>
      </header>

      <div id="form">
        <form action="">
          <label for="doggo_type">What kind of doggo are you looking for?</label>
          <input type="text">
        </input>
        </form>
      </div>

      <main class="site-content">
        <div id="aDog">
        </div>
        <div class="background-image-2">
          <img src="http://southpawpetservices.com/wp-content/uploads/2013/05/group-of-dogs-960x336.jpg" style="height:500px; width:1200px" alt="dog-pic">
        </div>
      </main>

      <footer class="site-footer">
        <p>&copy; 2018 Pupple. All Rights Reserved.</p>
      </footer>
      <script src="app.js" charset="utf-8"></script>
    </body>

  </div>
</template>




//All JavaScript goes here
<script>
const main1 = document.querySelector('#main1');
const API_KEY = '2911277f3a226d5574ee39f1cd3eb882';
const BASE_URL = 'https://cors-anywhere.herokuapp.com/http://api.petfinder.com/';

const doggoType = document.querySelector('#doggoType');
const type = document.querySelector('#type');
const url = `${BASE_URL}breed.list?key=${API_KEY}&format=json&animal=dog`

function getData() {
  fetch(url)
    .then(response => response.json())
    .then(json => {
      const data=json

      })
    }

getData()

const fetchMyApi = function() {
    fetch('myapigoeshere', {
    method: "POST",
    headers: new Headers({
        "content-type": "application/json"
    }),
    body: JSON.stringify({
        data
    })
}).then(function(response){
    return response.json()
}).then(function(json){
    console.log(json)
    const breeds = json.petfinder.breeds.breed;
    breeds.forEach(breed => {
      const breedOption = document.createElement('option');

      breedOption.textContent = breed.$t;
      type.appendChild(breedOption);
})
})

var select = document.querySelector('#type')

select.addEventListener('change', () => {
  event.preventDefault();
  var selectedDog = select.value;

  const petUrl = `${BASE_URL}pet.getRandom?key=${API_KEY}&output=basic&animal=dog&format=json&breed=${selectedDog}`
  fetch(petUrl)
    .then(response => response.json())
    .then(json => {
      console.log(json);
      const newDog = json.petfinder.pet;

      const option7 = document.createElement('img')
      option7.src = newDog.media.photos.photo[3].$t;
      document.querySelector('#aDog').appendChild(option7)

      const option0 = document.createElement('p')
      option0.innerHTML = 'Name: ' + newDog.name.$t
      document.querySelector('#aDog').appendChild(option0);

      const option1 = document.createElement('p')
      option1.innerHTML = 'Age: ' + newDog.age.$t
      document.querySelector('#aDog').appendChild(option1);

      const option6 = document.createElement('p')
      option6.innerHTML = 'Size: ' + newDog.size.$t;
      document.querySelector('#aDog').appendChild(option6);

      const option2 = document.createElement('p')
      option2.innerHTML = 'Description: ' + newDog.description.$t
      document.querySelector('#aDog').appendChild(option2);

      const option3 = document.createElement('p')
      option3.innerHTML = 'ID #: ' + newDog.id.$t
      document.querySelector('#aDog').appendChild(option3);

      const option4 = document.createElement('p')
      option4.innerHTML = 'Possible Mix? ' + newDog.mix.$t
      document.querySelector('#aDog').appendChild(option4);

      const option5 = document.createElement('p')
      option5.innerHTML = 'Sex: ' + newDog.sex.$t
      document.querySelector('#aDog').appendChild(option5);
    })
})

export default {
  name: 'PageTwo'
}
</script>



//All CSS goes here
<style lang="css">
body {
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
}

.site-header {
  display: flex;
  margin: -50px 20px 0px -10px;
  flex-direction: column;
  text-align: center;
  justify-content: space-around;
  width: 100%;
  font-family: Comfortaa;
  font-size: 50px;
  color: #51bbd9;
  position: fixed;
  z-index: 40;
}

.site-content {
  bottom: 0;
  width: 100%;
}

.phone-image {
  background-position: center;
  display: block;
  margin: -200px 20px 0px -420px;
  position: fixed;
  z-index: -1px;
  top: 0%;
}

.benton-image {
  display: block;
  margin: 150px 5px 75px 350px;
  position: fixed;
  z-index: 2;
}

.info-link, a:visited, a:hover {
  bottom: 162px;
  right: 40%;
  border-width: 1px;
  border-radius: 25px;
  justify-content: space-around;
  padding: 20px;
  background-color: grey;
  color: #51bbd9;
  font-family: Comfortaa;
  font-size: 20px;
  text-align: center;
  position: fixed;
  cursor: wait;
}

.tagline {
  font-family: Comfortaa;
  position: fixed;
  border-style: hidden;
  border-width: 1px;
  display: flex;
  flex-direction: column;
  font-size: 20px;
  text-align: center;
  margin-left: -5px;
  bottom: 25%;
  width: 100%;
}

.site-footer {
  position: fixed;
  border-style: hidden;
  border-width: 1px;
  display: flex;
  flex-direction: column;
  font-family: Comfortaa;
  font-size: 10px;
  text-align: center;
  bottom: 0%;
  width: 100%;
}

.background-image-2 {
  position: absolute;
  z-index: -1;
  margin-top: 20%;
  margin-left: 8%;
}

#form {
  display: flex;
  position: fixed;
  margin: 150px 20px 20px 550px;
  justify-content: center;
  font-family: Comfortaa;
  font-size: 40px;
  text-align: center;
  flex-direction: column;
}

#type {
  display: flex;
  width: 260px;
  font-size: 20px;
  font-family: Comfortaa;
}

#aDog {
  text-align: center;
  margin: 5px 20px 5px 20px;
  font-family: Comfortaa;
  font-size: 30px;
}


</style>
