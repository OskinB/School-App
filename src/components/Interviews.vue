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
      <div class="mobile-card" v-for="interview in interviewList" :key="interview.info">
        <div class="card-top">
          <h4>{{interview.date}}</h4>
          <div class="subject-icon">
            <img :src="getImgSubject(interview.subject)" alt="Áfangi" />
          </div>
        </div>
        <div class="mobile-card-info">
          <h2>{{interview.info}}</h2>
          <div class="selected-person">
            <h3>{{interview.teacherName}}</h3>
            <img :src="getImgUrl(interview.teacherAvatar)" alt="Kennari" />
          </div>
        </div>
      </div>
      <div class="mobile-btn-add" id="mb-interviews-btn" @click="showModal" v-if="isTeacher">
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
        <tr class="waitingList-card-info" v-for="interview in interviewList" :key="interview.info">
          <td>
            <h3>{{interview.date}}</h3>
          </td>

          <td>
            <div class="selected-subject">
              <img :src="getImgSubject(interview.subject)" alt="Áfangi" />
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
      v-bind="$props"
    />
  </div>
</template>

<script>
import ModalAddInterview from "./modals/AddInterview";

export default {
  props: {
    logedUserInfo: Object
  },
  components: {
    ModalAddInterview
  },
  data() {
    return {
      isModalVisible: false,
      isTeacher: false,
      interviewList: [
        {
          date: "24.apríl",
          subject: "JavaScript",
          info: "Munnlegt próf",
          teacherName: "Smári",
          teacherAvatar: "smari-avatar.svg",
          value: 20,
          time: []
        },
        {
          date: "11.apríl",
          subject: "Hönnun",
          info: "Figma próf",
          teacherName: "Jonathan",
          teacherAvatar: "jonni-avatar.svg",
          value: 10,
          time: []
        }
      ]
    };
  },
  methods: {
    getImgUrl(pic) {
      return require("../assets/" + pic);
    },
    getImgSubject(pic) {
      if (pic === "Vefþróun") {
        return require("../assets/vefthroun-img.svg");
      } else if (pic === "JavaScript") {
        return require("../assets/javascript-img.svg");
      } else if (pic === "Hönnun") {
        return require("../assets/figma-img.svg");
      } else if (pic === "HTML/CSS") {
        return require("../assets/html-img.svg");
      } else {
      }
    },
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    ModalAddInterview(addInterview) {
      this.interviewList.push(addInterview);
    },
    toggleAccess() {
      if (this.logedUserInfo.teacher) {
        this.isTeacher = true;
      }
    }
  },
  mounted() {
    this.toggleAccess();
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
