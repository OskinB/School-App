<template>
  <div>
    <!-- *** MOBILE *** -->
    <section id="mb-waitingList">
      <div class="mobile-card" v-for="help in waitingList" :key="help.helpInfo">
        <div class="card-top">
          <h4>{{ help.time }} mín</h4>
          <div class="subject-icon">
            <img :src="getImgSubject(help.subject)" alt="Áfangi" />
          </div>
        </div>
        <div class="mobile-card-info">
          <h2>{{ help.helpInfo }}</h2>
          <div class="selected-person">
            <h3>{{ help.studentName }}</h3>
            <img :src="getImgStudent(help.studentAvatar)" alt="Nemandi" />
          </div>
        </div>
      </div>

      <!-- *** TOGGLE IF Student/Teacher *** -->
      <div v-if="teacher === false">
        <div class="btn-holder-position">
          <div class="btn-back-holder">
            <a @click="backToSelect">Til baka</a>
          </div>
        </div>
        <div class="mobile-btn-add" @click="showModal">
          <h3>Bæta við</h3>
          <img src="../../assets/btn-add-icon.svg" alt="Bæta við" />
        </div>
      </div>
    </section>

    <!-- *** DESKTOP *** -->
    <section id="dt-waitingList">
      <h2 v-if="!waitingList.length">Enginn á biðlista</h2>
      <table class="card-table">
        <!-- *** Column title *** -->
        <tr class="card-info-title">
          <th>Áfangi</th>
          <th>Lýsing</th>
          <th>Kennari</th>
          <th>Nemandi</th>
          <th>Tími</th>
        </tr>

        <!-- *** Column info *** -->
        <tr
          class="waitingList-card-info"
          v-for="help in waitingList"
          :key="help.helpInfo"
        >
          <td>
            <div class="selected-subject">
              <img :src="getImgSubject(help.subject)" alt="Áfangi" />
              <h3>{{ help.subject }}</h3>
            </div>
          </td>

          <td>
            <h3>{{ help.helpInfo }}</h3>
          </td>

          <td>
            <div class="selected-person">
              <img :src="getImgTeacher(help.teacherAvatar)" alt="Kennari" />
              <h3>{{ help.teacherName }}</h3>
            </div>
          </td>

          <td>
            <div class="selected-person">
              <img :src="getImgStudent(help.studentAvatar)" alt="Nemandi" />
              <h3>{{ help.studentName }}</h3>
            </div>
          </td>

          <td>
            <h3>{{ help.time }} mín</h3>
          </td>
        </tr>
      </table>

      <!-- *** TOGGLE IF Student/Teacher *** -->
      <div v-if="teacher === false">
        <div class="btn-holder-position">
          <div class="btn-back-holder">
            <a @click="backToSelect">Til baka</a>
          </div>
        </div>
        <div class="btn-holder" id="dt-interviews-btn">
          <div class="btn-add-lg">
            <button type="button" class="btn-add-lg" @click="showModal">
              Bæta við
            </button>
          </div>
        </div>
      </div>
    </section>
    <ModalHelpRequest
      v-show="isModalVisible"
      @help-submitted="ModalAddHelp"
      @close="closeModal"
      v-bind="$props"
    />
  </div>
</template>

<script>
import ModalHelpRequest from "../modals/HelpRequest";

export default {
  name: "AllWaitingList",
  props: {
    logedUserInfo: Object,
    teacher: Boolean
  },
  components: {
    ModalHelpRequest
  },
  data() {
    return {
      isModalVisible: false,
      waitTime: 10,
      waitingList: [
        {
          subject: "Vefþróun",
          helpInfo: "Can't display from my PHP array",
          teacherName: "Pedro",
          teacherAvatar: "pedro-avatar.svg",
          studentName: "Klara",
          studentAvatar: "student1-avatar.svg",
          time: 5
        },
        {
          subject: "JavaScript",
          helpInfo: ".filter í .map er ekki að virka rétt",
          teacherName: "Smári",
          teacherAvatar: "smari-avatar.svg",
          studentName: "Siggi",
          studentAvatar: "student2-avatar.svg",
          time: 5
        }
      ]
    };
  },
  methods: {
    getImgSubject(pic) {
      if (pic === "Vefþróun") {
        return require("../../assets/vefthroun-img.svg");
      } else if (pic === "JavaScript") {
        return require("../../assets/javascript-img.svg");
      } else if (pic === "Hönnun") {
        return require("../../assets/figma-img.svg");
      } else if (pic === "HTML/CSS") {
        return require("../../assets/html-img.svg");
      }
    },
    getImgStudent(pic) {
      return require("../../assets/" + pic);
    },
    getImgTeacher(pic) {
      return require("../../assets/" + pic);
    },
    ModalAddHelp(addHelp) {
      this.waitingList.push(addHelp);
      this.waitTime += 5;
      this.$emit("get-total-time", this.waitTime);
    },
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    backToSelect() {
      this.$emit("back-to-select");
    }
  }
};
</script>

<style lang="scss">
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
