<template>
  <div class="login">
    <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
    <h1>Velkomin/n</h1>
    <div class="login-input">
      <input type="text" placeholder="Nafn" />
      <input type="text" placeholder="Lykilorð" />
      <div class="forgot-pw">
        <h4>Gleymt lykilorð?</h4>
      </div>
    </div>
    <div class="login-btns">
      <div class="btn-login">
        <h3>Skrá inn</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scope>
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

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
