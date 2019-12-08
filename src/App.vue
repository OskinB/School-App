<template>
  <div id="app">
    <div id="nav">
      <!-- <router-link to="/">Login</!-->
      <!-- <router-link to="/home">Home</router-link> -->
      <router-link v-if="authenticated" to="/login" v-on:click.native="logout()" replace>Logout</router-link>
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
        username: "sara",
        password: "sara",
        name: "Sara",
        avatar: "student-avatar.svg",
        teacher: false
      },
      teacher: {
        username: "smari",
        password: "smari",
        name: "Smári",
        avatar: "teacher-avatar.svg",
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
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

// #nav {
//   padding: 10px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
