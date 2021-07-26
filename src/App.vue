<template>
  <div id="app">
    <Navigation />
    <router-view class="container" :user="user" @logout="logout" />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation.vue'
import Firebase from 'firebase'
import db from './db.js' // eslint-disable-line

export default {
  name: 'app',
  data: function () {
    return {
      user: null
    }
  },
  components: {
    Navigation
  },
  methods: {
    logout: function () {
      Firebase.auth()
        .signOut()
        .then(() => {
          this.user = null
          this.$router.push('login')
        })
    }
  },
  mounted () {
    Firebase.auth().onAuthStateChanged(user => {
      if (user) {
        this.user = user.displayName
      }
    })
  }
}
</script>

<style lang="scss">
$primary: #05b2dd;
@import "node_modules/bootstrap/scss/bootstrap";
</style>
