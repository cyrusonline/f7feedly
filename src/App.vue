<template>
  <!-- App -->
  <div id="app">

    <!-- Statusbar -->
    <f7-statusbar></f7-statusbar>

    <!-- Main View -->
    <f7-view id="main-view" url="/" main></f7-view>


  </div>
</template>

<script>
import firebase from 'firebase'
  var config = {
  apiKey: "AIzaSyB9eiuN5GwxRpiceU_2X9U_D2kXRvzHccw",
  authDomain: "cloudfunction-9d075.firebaseapp.com",
  databaseURL: "https://cloudfunction-9d075.firebaseio.com",
  projectId: "cloudfunction-9d075",
  storageBucket: "cloudfunction-9d075.appspot.com",
  messagingSenderId: "351452593314"
};
firebase.initializeApp(config)
export default {
  name: 'App',
  methods: {
    handleBackButton() {
      // NOTE: The back button will behave differently depending on circumstance
      // If the side panel is open, close it
      if (document.querySelector('.panel-left.panel-active')) {
        // This will do nothing when the split-view is open
        return this.$f7.panel.close();
      }
      // Close modals
      // @TODO How to handle modals we shouldn't close like a login-screen?
      if (document.querySelector('.modal-in')) {
        return this.$f7.popover.close();
      }
      // If we have a back button, we want it to go back
      if (this.$f7.views.main.router.history.length > 1) {
        return this.$f7.views.main.router.back();
      }
      // Default to closing the app
      return window.navigator.app.exitApp();
    }
  },
  computed: {
    isiOS() {
      return window.isiOS;
    }
  },
  created() {
    document.addEventListener('backbutton', this.handleBackButton);
  }
};
</script>
