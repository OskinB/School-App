<template>
  <div>
    <!-- *** MOBILE/DESKTOP *** -->
    <section class="student-display">
      <div class="student-card">
        <div class="subject-icon">
          <img src="../../assets/figma-img.svg" alt="Áfangi" />
        </div>
        <div class="teacher-name">
          <h2>Jonathan</h2>
          <img src="../../assets/teacher-avatar.svg" alt="Kennari" />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: {},
  methods: {}
};
</script>


<style lang="scss" >
// *** MOBILE ***
.student-card {
  @include card;
  cursor: pointer;

  .subject-icon {
    @include mobilePill;
    @include mobileSubjectIcon;
  }
  .teacher-name {
    @include flex(row, space-between, center);
    color: $navy-blue;
    padding: 32px 16px 8px 24px;

    h2 {
      font-size: 24px;
      line-height: 34px;
      font-weight: bold;
      display: flex;
      align-items: center;
      text-align: center;
      margin: 16px 0;
    }

    img {
      height: 41px;
      width: 41px;
    }
  }
}

// ********** MEDIA QUERIES **********

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  .student-card {
    width: 212px;
    height: auto;
    margin: 64px 0;
    .teacher-name {
      @include flex(column-reverse, center, center);
      padding: 56px 53px 32px;

      h2 {
        margin: 32px 0 0;
      }
      img {
        height: 72px;
        width: 71px;
      }
    }
  }
}
</style>
