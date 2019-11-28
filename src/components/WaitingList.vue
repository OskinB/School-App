<template>
  <div class="ddd">
    <div class="page-title">
      <img src="../assets/waitinglist-img.svg" alt="Biðlisti" />
      <h1>Biðlisti</h1>
    </div>

    <div>
      <!-- *** STUDENT *** -->
      <!-- section class toggle Teacher or Student... who is loged in -->
      <section class="student-display">
        <div class="subject-icon">
          <img src="../assets/figma-img.svg" alt="Subject Icon" />
        </div>
        <div class="list-teacher">
          <h2>Jonathan</h2>
          <img src="../assets/jonni-avatar.svg" alt="Jonathan" />
        </div>
      </section>

    </div>
    <!-- *** Teacher *** -->
    <!-- <section class="teacher-display" id="mb-waiting-list">
      <div class="subject-icon">
        <img src="../assets/figma-img.svg" alt="Subject Icon" />
      </div>
      <div class="list-teacher">
        <h2>Jonathan</h2>
        <img src="../assets/jonni-avatar.svg" alt="Jonathan" />
      </div>
    </section>

    <section class="teacher-display" id="dt-waiting-list">
      <div class="subject-icon">
        <img src="../assets/figma-img.svg" alt="Subject Icon" />
      </div>
      <div class="list-teacher">
        <h2>Jonathan</h2>
        <img src="../assets/jonni-avatar.svg" alt="Jonathan" />
      </div>
    </section>-->
  </div>
</template>

<script>
export default {};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scope>
.page-title {
  @include flex(row, flex-start, center);
  color: $navy-blue;

  h1 {
    font-size: 24px;
    margin-left: 8px;
  }
}

.student-display {
  background-color: $white;
  box-shadow: 0px 5px 5px rgba(0, 0, 0, 0.05);
  border-radius: 10px;
  position: relative;
  margin: 24px;

  .subject-icon {
    position: absolute;
    right: 0;
    top: -25px;
  }
  .list-teacher {
    @include flex(row, space-around, center);
    color: $navy-blue;
    padding: 24px 0;
    margin: 32px;
    h2 {
      font-size: 24px;
      line-height: 34px;
      display: flex;
      align-items: center;
      text-align: center;
      margin: 16px 0;
    }
  }
}

// Þegar er mobile
@media only screen and (max-width: 900px) {
  #dt-login {
    display: none;
  }
}

// Þegar er desktop
@media only screen and (min-width: 900px) {
  //   #mb-waiting-list {
  //     display: none;
  //   }

  .student-display {
    width: 212px;
    .list-teacher {
      @include flex(column-reverse, center, center);
      padding: 56px 72px;
    }
  }
}
</style>
