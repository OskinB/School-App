<template>
  <div>
    <!-- *** MOBILE *** -->
    <section id="mb-waitingList">
      <div class="mobile-card">
        <div class="card-top">
          <h4>10:00</h4>
          <div class="subject-icon">
            <img src="../../assets/figma-img.svg" alt="Áfangi" />
          </div>
        </div>
        <div class="mobile-card-info">
          <h2>Hönnunarpæling</h2>
          <div class="selected-person">
            <h3>Ósk Björns</h3>
            <img src="../../assets/student-avatar.svg" alt="Nemandi" />
          </div>
        </div>
      </div>
      <!-- * IF STUDENT - SHOW * -->
      <div class="mobile-btn-add">
        <h3>Bæta við</h3>
        <img src="../../assets/btn-add-icon.svg" alt="Bæta við" />
      </div>
    </section>

    <!-- *** DESKTOP *** -->
    <section id="dt-waitingList">
      <table class="card-table">
        <tr class="card-info-title">
          <th>Áfangi</th>
          <th>Lýsing</th>
          <th>Kennari</th>
          <th>Nemandi</th>
          <th>Tími</th>
        </tr>

        <tr class="waitingList-card-info">
          <td>
            <div class="selected-subject">
              <h3>Figma</h3>
              <img src="../../assets/figma-img.svg" alt="Áfangi" />
            </div>
          </td>

          <td>
            <h3>Hönnunarpælingar</h3>
          </td>

          <td>
            <div class="selected-person">
              <h3>Jonathan</h3>
              <img src="../../assets/teacher-avatar.svg" alt="Kennari" />
            </div>
          </td>

          <td>
            <div class="selected-person">
              <h3>Ósk Björns</h3>
              <img src="../../assets/student-avatar.svg" alt="Nemandi" />
            </div>
          </td>

          <td>
            <h3>5 mín</h3>
          </td>
          <td>
            <img src="../../assets/arrow-down.svg" alt="Sjá meira" />
          </td>
          <!-- * IF TEACHER - SHOW ON EVERY CARD* -->
          <!-- * IF STUDENT - SHOW ON YOUR OWN CARD* -->
          <!-- <div class="close-icon">
            <img src="../../assets/x-icon.svg" alt="Eyða" />
          </div>-->
        </tr>
      </table>

      <div class="btn-holder" id="dt-interviews-btn">
        <div class="btn-add-lg">
          <a class="btn-add-lg" href="#open-modal">Bæta við</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {};
</script>


<style lang="scss" scope>
// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
  #dt-waitingList {
    display: none;
  }
}
// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  #mb-waitingList {
    display: none;
  }
}
</style>
