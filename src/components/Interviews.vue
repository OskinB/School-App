<template>
  <div>
    <div class="page-title">
      <img src="../assets/interviews-icon.svg" alt="Viðtöl" />
      <h1>Viðtöl</h1>
    </div>

    <section class="student-display">
      <div class="teachers-card">
        <div class="card-top">
          <h4>10:00</h4>
          <div class="subject-icon">
            <img src="../assets/figma-img.svg" alt="Áfangi" />
          </div>
        </div>
        <div class="waiting-list-info">
          <h2>Hönnunarpæling</h2>
          <div class="selected-person">
            <h3>Ósk Björns</h3>
            <img src="../assets/student-avatar.svg" alt="Kennari" />
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="mobile-btn-add">
        <h3>Bæta við</h3>
        <img src="../assets/btn-add-icon.svg" alt="Bæta við" />
      </div>
    </section>

    <section>
      <div class="btn-add">
        <h3>Skoða</h3>
      </div>
    </section>
    <hr />
    <section>
      <div class="btn-confirm">
        <h3>Staðfesta</h3>
      </div>
    </section>
  </div>
</template>

<script>
export default {};
</script>


<style lang="scss" scope>
// *** TEACHERS & STUDENTS ***
.page-title {
  @include pageTitle;
}

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
