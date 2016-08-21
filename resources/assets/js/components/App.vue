<template>
<div>
    <div class="window-content">
        <div class="pane-group">
            <sidebar></sidebar>

            <div class="pane">
              <router-view></router-view>
            </div>
        </div>
    </div>
</div>
  </template>
 
 <script>
  import {Auth} from '../index'
  import Sidebar from './shared/Sidebar.vue';

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
        Sidebar
    }
  }
  </script>