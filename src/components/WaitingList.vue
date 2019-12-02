<template>
  <div>
    <div class="page-title">
      <div class="student-display">
        <div class="student-title">
          <img src="../assets/waitinglist-img.svg" alt="Biðlisti" />
          <h1>Biðlisti</h1>
        </div>
      </div>
      <div class="teacher-display">
        <h2 class="dt-waiting-time">10 mín</h2>
      </div>
    </div>
    <!-- *** STUDENT *** -->
    <!-- section class toggle Teacher or Student... who is loged in -->
    <!-- <section class="student-display">
      <div class="students-card">
        <div class="subject-icon">
          <img src="../assets/figma-img.svg" alt="Áfangi" />
        </div>
        <div class="list-teacher">
          <h2>Jonathan</h2>
          <img src="../assets/teacher-avatar.svg" alt="Kennari" />
        </div>
      </div>
    </section>-->

    <!-- *** TEACHER MOBILE*** -->
    <section class="teacher-display" id="mb-teacher-waiting">
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

    <!-- *** TEACHER DESKTOP*** -->
    <section class="teacher-display" id="dt-teacher-waiting">
      <table>
        <tr class="info-title">
          <th>Áfangi</th>
          <th>Lýsing</th>
          <th>Kennari</th>
          <th>Nemandi</th>
          <th>Tími</th>
        </tr>

        <tr class="teachers-card-elements">
          <td>
            <div class="selected-subject">
              <h3>Figma</h3>
              <img src="../assets/figma-img.svg" alt="Áfangi" />
            </div>
          </td>

          <td>
            <h3 class="td-info">Hönnunarpælingar</h3>
          </td>

          <td>
            <div class="selected-person">
              <h3>Jonathan</h3>
              <img src="../assets/teacher-avatar.svg" alt="Kennari" />
            </div>
          </td>

          <td>
            <div class="selected-person">
              <h3>Ósk Björns</h3>
              <img src="../assets/student-avatar.svg" alt="Nemandi" />
            </div>
          </td>

          <td>
            <h3 class="td-time">5 mín</h3>
          </td>
          <td>
            <img src="../assets/arrow-down.svg" alt="Sjá meira" />
          </td>
          <div class="close-icon">
            <img src="../assets/x-icon.svg" alt="Eyða" />
          </div>
        </tr>
      </table>
    </section>
  </div>
</template>

<script>
export default {};
</script>


<style lang="scss" scope>
.close-icon {
  @include mobilePill;
  @include flex(row, center, center);
  position: absolute;
  padding: 6px;
  top: 306px;
  right: 23px;

  img {
    height: 20px;
    width: 20px;
  }
}

// *** TEACHERS & STUDENTS ***
.page-title {
  @include flex(row, space-between, center);
  color: $navy-blue;

  .student-title {
    @include flex(row, flex-start, center);
    h1 {
      font-size: 24px;
      // *Vantar: font-weight: 500/medium;
      margin-left: 8px;
    }
  }
  h2 {
    font-size: 32px;
    line-height: 46px;
    font-weight: bold;
  }
}

.selected-person,
.selected-subject {
  @include flex(row, flex-start, center);
  margin-top: 8px;
  h3 {
    font-size: 16px;
    line-height: 23px;
  }
  img {
    height: 32px;
    width: 32px;
    margin: 0 16px;
  }
}

.subject-icon {
  @include mobilePill;
  @include mobileSubjectIcon;
}

// *** STUDENTS MOBILE***
.students-card {
  @include card;

  .subject-icon {
    @include mobileSubjectIcon;
    @include mobilePill;
  }
  .list-teacher {
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

// *** TEACHERS MOBILE ***
.teachers-card {
  @include card;
  color: $navy-blue;

  .card-top {
    @include flex(row, flex-end, center);

    h4 {
      @include mobilePill;
      position: absolute;
      right: 80px;
      top: -15px;
      font-size: 16px;
      line-height: 23px;
      font-weight: bold;
    }
  }
  .waiting-list-info {
    @include flex(column, flex-start, flex-start);
    padding: 16px 0 16px 24px;

    h2 {
      font-size: 16px;
      line-height: 23px;
      font-weight: bold;
    }
  }
}

// *** TEACHERS DESKTOP ***
table {
  width: 100%;
  font-size: 16px;
  line-height: 23px;

  .info-title {
    margin: 32px 0;
    color: $grey;
  }

  .teachers-card-elements {
    @include card;
    color: $navy-blue;
  }

  th,
  td {
    text-align: left;
    padding: 24px 32px;
    vertical-align: middle;
  }
  td > div {
    @include flex(row, flex-start, center);
  }
}

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
  #dt-teacher-waiting {
    display: none;
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  #mb-teacher-waiting {
    display: none;
  }

  .dt-waiting-time {
    margin-right: 40px;
  }

  .student-display {
    width: 212px;
    height: auto;
    margin: 64px 0;
    .list-teacher {
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
