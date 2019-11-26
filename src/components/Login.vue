<template>
  <div>
    <div class="hello" id="mb-login">
      <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
      <h1>Velkomin/n MOBILE</h1>
      <input type="text" placeholder="Nafn" />
      <input type="text" placeholder="Lykilorð" />
      <small>Gleymt lykilorð?</small>
      <button>Skrá inn</button>
      <button>Búa til aðgang</button>
    </div>
    <div class="hello" id="dt-login">
      <img src="../assets/Tskoli-logo.svg" alt="Tækniskólinn" />
      <h1>Velkomin/n DESKTOP</h1>
      <input type="text" placeholder="Nafn" />
      <input type="text" placeholder="Lykilorð" />
      <small>Gleymt lykilorð?</small>
      <button>Skrá inn</button>
      <button>Búa til aðgang</button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scope lang="scss">
@import "../sass/_variables";

h1 {
  color: $bright-orange;
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
