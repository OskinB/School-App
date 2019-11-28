<template>
  <div class="login-page">
    <Login />
  </div>
</template>

<script>
// @ is an alias to /src
import Login from "@/components/Login.vue";

export default {
  name: "loginPage",
  components: {
    Login
  }
};
</script>

<style lang="scss" scope>
.login-page {
  width: 400px;
  margin: 0 auto;
}
</style>
