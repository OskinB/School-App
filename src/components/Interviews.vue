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
      <div class="mobile-card" v-for="interview in interviewList" v-bind:key="interview.info">
        <div class="card-top">
          <h4>{{interview.date}}</h4>
          <div class="subject-icon">
            <img src="../assets/javascript-img.svg" alt="Áfangi" />
          </div>
        </div>
        <div class="mobile-card-info">
          <h2>{{interview.info}}</h2>
          <div class="selected-person">
            <h3>{{interview.teacherName}}</h3>
            <img src="../assets/teacher-avatar.svg" alt="Kennari" />
          </div>
        </div>
      </div>
      <div class="mobile-btn-add" id="mb-interviews-btn" v-if="isTeacher" @click="showModal">
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
          v-bind:key="interview.info"
        >
          <td>
            <h3>{{interview.date}}</h3>
          </td>

          <td>
            <div class="selected-subject">
              <img :src="getImgUrl(interview.subjectIcon)" alt="Áfangi" />
              <h3>{{interview.subject}}</h3>
            </div>
          </td>

          <td>
            <h3>{{interview.info}}</h3>
          </td>

          <td>
            <div class="selected-person">
              <img :src="getImgUrl(interview.teacherAvatar)" alt="Kennari" />
              <h3>{{interview.teacherName}}</h3>
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
          <button type="button" class="btn-add-lg" @click="showModal">Bæta við</button>
        </div>
      </div>
    </section>
    <ModalAddInterview
      v-show="isModalVisible"
      @interview-submitted="ModalAddInterview"
      @close="closeModal"
    />
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
      isModalVisible: false,
      interviewList: [
        {
          date: "24.apríl",
          subject: "JavaScript",
          subjectIcon: "javascript-img.svg",
          info: "Munnlegt próf",
          teacherName: "Smári",
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
    },
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    ModalAddInterview(addInterview) {
      this.interviewList.push(addInterview);
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
      font-weight: 500;
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
