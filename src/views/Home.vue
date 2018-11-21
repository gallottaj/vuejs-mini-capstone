<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <p v-for="product in products"> {{product.name}}</p> -->
     <div class="container">
      <div class="row">
        <div class="col-sm-4" v-for="product in products">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">name: {{ product.name }}</h5>
              <p class="card-text">price: {{ product.price }}</p>
              <img v-bind:src="product.image_url" width="100px">
              <p class="card-text">description: {{product.description}}</p>
              <a href="/show.html" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
</style>

<script>

var axios = require('axios');

export default {
  data: function() {
    console.log('index action');
    return {
      message: "Welcome to Vue.js!",
      products: []
    };
  },
  created: function() {
    axios.get('http://localhost:3000/api/products/').then(function(response) {
      console.log(response.data);
      this.products = response.data;
    }.bind(this));
  },
  methods: {},
  computed: {}
};
</script>