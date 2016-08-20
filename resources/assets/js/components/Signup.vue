<template>
    <div class="col-sm-4 col-sm-offset-4">
      <h2>Signup</h2>
      <p>Signup for an account.</p>
      <div class="alert alert-danger" v-if="error">
        <p>{{ error }}</p>
      </div>

      <div class="form-group">
              <input
                type="text"
                class="form-control"
                placeholder="Enter your name"
                v-model="credentials.name"
              >
            </div>

      <div class="form-group">
        <input
          type="text"
          class="form-control"
          placeholder="Enter your email"
          v-model="credentials.email"
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
      <button class="btn btn-primary" @click="submit()">Signup Free</button>
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
            name: this.credentials.name,
            email: this.credentials.email,
            password: this.credentials.password
          }

          // We need to pass the component's this context
          // to properly make use of http in the auth service
          Auth.signup(this, credentials, 'login')
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