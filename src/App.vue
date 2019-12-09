<template>
  <div id="app">
    <div id="nav" v-show="authenticated">
      <router-link v-if="authenticated" to="/login" v-on:click.native="logout()" replace>Útskráning</router-link>
    </div>
    <router-view
      @authenticated="setAuthenticated"
      @logedUserInfo="userInfo"
      v-bind:logedUserInfo="logedUserInfo"
    />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      authenticated: false,
      logedUserInfo: {},
      student: {
        username: "as",
        password: "as",
        name: "Ósk",
        avatar: "student0-avatar.svg",
        teacher: false
      },
      teacher: {
        username: "smari",
        password: "smari",
        name: "Smári",
        avatar: "smari-avatar.svg",
        teacher: true
      }
    };
  },
  mounted() {
    if (!this.authenticated) {
      this.$router.replace({ name: "LoginPage" });
    }
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout() {
      this.authenticated = false;
    },
    userInfo(info) {
      this.logedUserInfo = info;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Raleway", sans-serif;
  text-align: right;
}

#nav {
  padding: 16px 0;

  a {
    font-weight: bold;
    color: $light-blue;
    font-size: 14px;
    padding: 8px 8px;
    margin: 8px 8px;

    &:hover {
      color: $navy-blue;
    }
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  #nav {
    padding: 24px 0;

    a {
      font-size: 16px;
      padding: 8px 16px;
      margin: 8px 56px;
    }
  }
}
</style>
