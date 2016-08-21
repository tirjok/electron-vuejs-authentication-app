<template>
    <div class="pane pane-sm sidebar">
        <ul class="list-group">
          <li class="list-group-item">
            <img class="img-circle media-object pull-left" src="http://photonkit.com/assets/img/avatar5.png" width="32" height="32">
            <div class="media-body">
              <strong>ETMS</strong>
              <p>username</p>
            </div>
          </li>
        </ul>

        <nav class="nav-group">
          <h5 class="nav-group-title">Favorites</h5>
          <a v-link="'home'" class="nav-group-item">
              <span class="icon icon-home"></span>
              Home
            </a>

          <a v-link="'login'" v-if="!user.authenticated" class="nav-group-item">
          <span class="icon icon-login"></span>
          Login</a>

          <a v-link="'signup'" v-if="!user.authenticated" class="nav-group-item">
          <span class="icon icon-user-add"></span>
          Sign Up</a>

          <a class="nav-group-item" v-link="'secretquote'" v-if="user.authenticated">
          <span class="icon icon-database"></span>
          Secret Quote
          </a>
          <a class="nav-group-item" v-link="'login'" v-if="user.authenticated" @click="logout()">
          <span class="icon icon-logout"></span>
          Logout
          </a>

        </nav>
    </div>
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