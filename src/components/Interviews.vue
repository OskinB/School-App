<template>
  <div class="page-holder">
    <section class="page-title">
      <div class="main-title">
        <img src="../assets/interviews-icon.svg" alt="Viðtöl" />
        <h1>Viðtöl</h1>
      </div>
    </section>

    <!-- *** MOBILE*** -->
    <section id="mb-interviews">
      <div class="mobile-card">
        <div class="card-top">
          <h4>24.apríl</h4>
          <div class="subject-icon">
            <img src="../assets/javascript-img.svg" alt="Áfangi" />
          </div>
        </div>
        <div class="mobile-card-info">
          <h2>Munnlegt próf</h2>
          <div class="selected-person">
            <h3>Ellert Smári</h3>
            <img src="../assets/teacher-avatar.svg" alt="Kennari" />
          </div>
        </div>
      </div>
      <div class="mobile-btn-add" id="mb-interviews-btn">
        <h3>Bæta við</h3>
        <img src="../assets/btn-add-icon.svg" alt="Bæta við" />
      </div>
    </section>

    <!-- *** DESKTOP *** -->
    <section id="dt-interviews">
      <h2 v-if="!interviewList.length">Ekkert viðtal skráð</h2>
      <table class="card-table">
        <!-- *** Column title *** -->
        <tr class="card-info-title">
          <th>Dags.</th>
          <th>Áfangi</th>
          <th>Lýsing</th>
          <th>Kennari</th>
          <th>Vægi</th>
        </tr>

        <!-- *** Column info *** -->
        <tr
          class="waitingList-card-info"
          v-for="interview in interviewList"
          v-bind:key="interview.id"
        >
          <td>
            <h3>{{interview.date}}</h3>
          </td>

          <td>
            <div class="selected-subject">
              <h3>{{interview.subject}}</h3>
              <img :src="getImgUrl(interview.subjectIcon)" alt="Áfangi" />
            </div>
          </td>

          <td>
            <h3>{{interview.info}}</h3>
          </td>

          <td>
            <div class="selected-person">
              <h3>{{interview.teacherName}}</h3>
              <img :src="getImgUrl(interview.teacherAvatar)" alt="Kennari" />
            </div>
          </td>

          <td>
            <h3>{{interview.value}}%</h3>
          </td>
          <td>
            <div class="btn-add-sm">
              <h3>Skoða</h3>
            </div>
          </td>
        </tr>
      </table>

      <div class="btn-holder" id="dt-interviews-btn" v-if="isTeacher">
        <div class="btn-add-lg">
          <a class="btn-add-lg" href="#open-inter">Bæta við</a>
        </div>
      </div>
    </section>
    <ModalAddInterview />
  </div>
</template>

<script>
import ModalAddInterview from "./modals/AddInterview";

export default {
  props: ["isTeacher"],
  components: {
    ModalAddInterview
  },
  data() {
    return {
      interviewList: [
        {
          date: "24.apríl",
          subject: "JavaScript",
          subjectIcon: "javascript-img.svg",
          info: "Munnlegt próf",
          teacherName: "Ellert Smári",
          teacherAvatar: "teacher-avatar.svg",
          value: 20
        },
        {
          date: "11.apríl",
          subject: "Hönnun",
          subjectIcon: "figma-img.svg",
          info: "Figma próf",
          teacherName: "Jonathan",
          teacherAvatar: "teacher-avatar.svg",
          value: 10
        }
      ]
    };
  },
  methods: {
    getImgUrl(pic) {
      return require("../assets/" + pic);
    }
  }
};
</script>


<style lang="scss" >
.page-title {
  color: $navy-blue;
  margin: 32px 0 48px;

  .main-title {
    @include flex(row, flex-start, center);
    h1 {
      font-size: 24px;
      // *Vantar: font-weight: 500/medium;
      margin-left: 8px;
    }
  }
}

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
  #dt-interviews {
    display: none;
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  #mb-interviews {
    display: none;
  }
}
</style>
