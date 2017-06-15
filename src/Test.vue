<template>
  <div id="app">
    <input id="searchTextField" type="text" v-model="address">
    <button @click="getLoc()">Get loc details</button>
    <button @click="getLocPhoto()">Get loc photo</button>
    <img v-bind:src="this.response">
    <!--{{this.response}}-->
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      address: '',
      response : "Y'a rien"
    }
  },
  methods: {
    getLoc() {
      var xmlHttp = new XMLHttpRequest();
      xmlHttp.open("GET", "https://maps.googleapis.com/maps/api/geocode/json?address="+this.address+"&key=AIzaSyCUEEzTpu8BzuQ2te4yY0gBzvQ6ax7w_wA"
, false);
      xmlHttp.send();
      this.response = xmlHttp.response;
      this.response = JSON.parse(this.response);
    },
    getLocPhoto() {
      this.response = "https://maps.googleapis.com/maps/api/streetview?size=600x400&location="+this.address+"&fov=120&heading=0&pitch=10&key=AIzaSyCUEEzTpu8BzuQ2te4yY0gBzvQ6ax7w_wA";
    }
  },
  mounted: {
    loadPlaces() {
      var defaultBounds = new google.maps.LatLngBounds(
      new google.maps.LatLng(-33.8902, 151.1759),
      new google.maps.LatLng(-33.8474, 151.2631));

      var input = document.getElementById('searchTextField');
      var options = {
        bounds: defaultBounds,
        types: ['establishment']
      };

      autocomplete = new google.maps.places.Autocomplete(input, options);
    }
  }
}

</script>

<style>

</style>
