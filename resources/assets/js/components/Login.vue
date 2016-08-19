<template>
    <div class="col-sm-4 col-sm-offset-4">
      <h2>Log In</h2>
      <p>Log in to your account to get some great quotes.</p>
      <div class="alert alert-danger" v-if="error">
        <p>{{ error }}</p>
      </div>
      <div class="form-group">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your username"
          v-model="credentials.username"
        >
      </div>
      <div class="form-group">
        <input
          type="password"
          class="form-control"
          placeholder="Enter your password"
          v-model="credentials.password"
        >
      </div>
      <button class="btn btn-primary" @click="submit()">Access</button>
    </div>
  </template>

  <script>
  import {Auth} from '../index'
  
  export default {
    data() {
      return {
        // We need to initialize the component with any
        // properties that will be used in it
        credentials: {
          username: '',
          password: ''
        },
        error: ''
      }
    },
    methods: {
      submit() {
        var credentials = {
          grant_type: 'password',
          client_id: '07dbf35a289cfdcab10c982b529cbb75',
          client_secret: '731cc0f2450defb3fe707ca467a286c9',
          username: this.credentials.username,
          password: this.credentials.password
        }

        // We need to pass the component's this context
        // to properly make use of http in the auth service
        Auth.login(this, credentials, 'secretquote')
      }
    },
    route: {
      // Check the users auth status before
      // allowing navigation to the route
      canActivate() {
        return !Auth.user.authenticated
      }
    }
  }
  </script>