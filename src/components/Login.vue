<template>
  <small>
    <small class="login" id="mb-login">
      <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
      <h1>Velkomin/n MOBILE</h1>
      <div class="login-input">
        <input type="text" placeholder="Nafn" />
        <input type="text" placeholder="Lykilorð" />
      </div>
      <small>Gleymt lykilorð?</small>
      <button>Skrá inn</button>
      <button>Búa til aðgang</button>
    </small>
    <div class="login" id="dt-login">
      <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
      <h1>Velkomin/n DESKTOP</h1>
      <div class="login-input">
        <input type="text" placeholder="Nafn" />
        <input type="text" placeholder="Lykilorð" />
      </div>
      <small>Gleymt lykilorð?</small>
      <button>Skrá inn</button>
      <button>Búa til aðgang</button>
    </div>
  </small>
</template>

<script>
export default {};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scope>
.login {
  display: flex;
  flex-direction: column;
  h1 {
    color: $bright-orange;
  }
}
.login-input {
  margin: 20px;
}

// Þegar er mobile
@media only screen and (max-width: 900px) {
  #dt-login {
    display: none;
  }
}

// Þegar er desktop
@media only screen and (min-width: 900px) {
  #mb-login {
    display: none;
  }
}
</style>
