<template>
    <div class="padded-more">
      <h1>Get a Secret Chuck Norris Quote!</h1>
      <button class="btn btn-warning" v-on:click="getQuote()">Get a Quote</button>
      <div class="quote-area" v-if="quote">
        <h2><blockquote>{{ quote }}</blockquote></h2>      
      </div>
    </div>
  </template>


  <script>
  import {Auth} from '../index'

  export default {
    data() {
      return {
        quote: ''
      }
    },
    methods: {
      getQuote() {
        this.quote = 'This is Secret'
      }
    },
    route: {
      // Check the users auth status before
      // allowing navigation to the route
      canActivate() {
        return Auth.user.authenticated
      }
    }
  }
  </script>