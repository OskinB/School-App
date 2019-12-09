<template>
  <div id="app">
    <div id="nav" v-show="authenticated">
      <router-link v-if="authenticated" to="/login" @click.native="logout()" replace>
        <img src="./assets/log-out.svg" alt="img" />
        <h2>Útskráning</h2>
      </router-link>
    </div>
    <router-view
      @authenticated="setAuthenticated"
      @logedUserInfo="userInfo"
      :logedUserInfo="logedUserInfo"
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
        username: "sm",
        password: "sm",
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
  @include flex(row, flex-end, center);

  a {
    @include flex(row, flex-end, center);
    padding: 8px;
    margin: 8px 8px 0 16px;
    h2 {
      font-size: 14px;
      font-weight: bold;
      color: $light-blue;
      margin-left: 8px;
    }
    img {
      height: 16px;
      width: 16px;
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
      margin: 8px 32px;
      h2 {
        display: none;
        font-size: 18px;
        margin-left: 8px;
      }

      &:hover {
        h2 {
          display: block;
        }
      }

      img {
        height: 24px;
        width: 24px;
      }
    }
  }
}
</style>
