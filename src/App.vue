<template>
  <div id="app">
    <Navigation :user="user" @logout="logout" />
    <router-view class="container" :user="user" @logout="logout" @addMeeting="addMeeting" />
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
    },
    addMeeting: function (payload) {
      db.collection('users')
        .doc(this.user.uid)
        .collection('meetings')
        .add({
          name: payload,
          createdAd: Firebase.firestore.FieldValue.serverTimestamp()
        })
    }
  },
  mounted () {
    Firebase.auth().onAuthStateChanged(user => {
      if (user) {
        this.user = user
      }
    })
  }
}
</script>

<style lang="scss">
$primary: #05b2dd;
@import "node_modules/bootstrap/scss/bootstrap";
</style>
