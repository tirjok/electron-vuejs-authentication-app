<template>
    <nav class="navbar navbar-default">
      <div class="container">
        <ul class="nav navbar-nav">
          <li><a v-link="'home'">Home</a></li>
          <li><a v-link="'login'" v-if="!user.authenticated">Login</a></li>
          <li><a v-link="'signup'" v-if="!user.authenticated">Sign Up</a></li>
          <li><a v-link="'secretquote'" v-if="user.authenticated">Secret Quote</a></li>
          <li><a v-link="'login'" v-if="user.authenticated" @click="logout()">Logout</a></li>
        </ul>
      </div>
    </nav>
</template>

<script>
import {Auth} from '../../index';

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
    }
  }
</script>