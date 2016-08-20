<template>
  <div>

    <navbar></navbar>

    <div class="container">
      <router-view></router-view>
    </div>
  </div>
  </template>
 
 <script>
  import {Auth} from '../index'
  import Navbar from './shared/Navbar.vue';

  export default {
    data() {
      return {
        user: Auth.user
      }
    },
    methods: {
      logout() {
        Auth.logout()
      }
    },

    components: {
        Navbar
    }
  }
  </script>