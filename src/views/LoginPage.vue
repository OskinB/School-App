<template>
  <div class="login">
    <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
    <h1>Velkomin/n</h1>
    <div class="login-input">
      <input
        type="text"
        v-model="input.username"
        @click="showError"
        placeholder="Notendanafn"
        required
      />
      <input
        type="password"
        v-model="input.password"
        @click="showError"
        placeholder="Lykilorð"
        required
      />
      <div class="forgot-pw">
        <h4>Gleymt lykilorð?</h4>
      </div>
    </div>
    <div class="error">
      <h3 v-show="error.show">{{ error.message }}</h3>
    </div>
    <div class="btn-holder-modal">
      <div class="btn-login">
        <button type="button" class="btn-login" @click="login()">
          Skrá inn
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginPage",
  data() {
    return {
      input: {
        username: "",
        password: ""
      },
      error: {
        message: "",
        show: false
      }
    };
  },
  methods: {
    login() {
      if (this.input.username != "" && this.input.password != "") {
        if (
          this.input.username == this.$parent.student.username &&
          this.input.password == this.$parent.student.password
        ) {
          this.$emit("authenticated", true);
          this.$emit("logedUserInfo", this.$parent.student);
          this.$router.replace({ name: "Home" });
        } else if (
          this.input.username == this.$parent.teacher.username &&
          this.input.password == this.$parent.teacher.password
        ) {
          this.$emit("authenticated", true);
          this.$emit("logedUserInfo", this.$parent.teacher);
          this.$router.replace({ name: "Home" });
        } else {
          this.error.show = true;
          this.error.message = "Notendanafn og/eða lykilorð er rangt";
          console.log("The username and / or password is incorrect");
        }
      } else {
        this.error.show = true;
        this.error.message = "Skráðu notendanafn og lykilorð";

        console.log("A username and password must be present");
      }
    },
    showError() {
      this.error.show = false;
    }
  }
};
</script>

<style lang="scss">
.login {
  @include flex(column, center, center);
  background-color: $white;
  height: 100vh;

  img {
    margin-top: 32px;
  }

  .login-input {
    @include flex(column, center, center);

    input {
      background-color: $light-grey;
      border-radius: 5px;
      color: black;
      border: none;
      width: 270px;
      margin: 8px 0;
      padding: 1rem;
      cursor: pointer;

      &:focus {
        outline: 1px solid $light-blue;
      }
    }

    .forgot-pw {
      width: 100%;

      h4 {
        font-size: 14px;
        line-height: 20px;
        color: $grey;
        text-align: right;
        cursor: pointer;
      }
    }
  }
  .error {
    margin: 8px;
    font-size: 14px;
    color: crimson;
    height: 14px;
  }

  h1 {
    font-size: 24px;
    line-height: 34px;
    color: $navy-blue;
    font-weight: bold;
    margin: 24px 0 48px;
  }

  .login-btns {
    margin: 40px 0;
  }
}
</style>
