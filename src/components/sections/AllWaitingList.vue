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
        <tr class="waitingList-card-info" v-for="help in waitingList" v-bind:key="help.helpInfo">
          <td>
            <div class="selected-subject">
              <h3>{{help.subject}}</h3>
              <!-- <img :src="getImgUrl(help.subjectIcon)" alt="Áfangi" /> -->
            </div>
          </td>

          <td>
            <h3>{{help.helpInfo}}</h3>
          </td>

          <td>
            <div class="selected-person">
              <h3>{{help.teacherName}}</h3>
              <!-- <img :src="getImgUrl(help.teacherAvatar)" alt="Kennari" /> -->
            </div>
          </td>

          <td>
            <div class="selected-person">
              <h3>{{help.studentName}}</h3>
              <!-- <img :src="getImgUrl(help.studentAvatar)" alt="Nemandi" /> -->
            </div>
          </td>

          <td>
            <h3>{{help.time}} mín</h3>
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

      <!-- * IF STUDENT - SHOW ADD BTN * -->
      <!-- <div class="btn-holder" id="dt-interviews-btn" v-if="teacherIs === false"> -->
      <div class="btn-holder" id="dt-interviews-btn">
        <div class="btn-add-lg">
          <button type="button" class="btn-add-lg" @click="showModal">Bæta við</button>
        </div>
      </div>
    </section>
    <ModalHelpRequest v-show="isModalVisible" @help-submitted="ModalAddHelp" @close="closeModal" />
  </div>
</template>

<script>
import ModalHelpRequest from "../modals/HelpRequest";
import AllWaitingList from "@/components/sections/AllWaitingList";

export default {
  name: "AllWaitingList",
  props: ["teacherIs"],
  components: {
    ModalHelpRequest
  },
  props: {},
  data() {
    return {
      isModalVisible: false,
      waitTime: 10,
      isTeacher: "",
      waitingList: [
        {
          subject: "Vefþróun",
          subjectIcon: "figma-img.svg",
          helpInfo: "Skil ekki mixins",
          teacherName: "Pedro",
          teacherAvatar: "teacher-avatar.svg",
          studentName: "Ósk",
          studentAvatar: "student-avatar.svg",
          time: 5
        },
        {
          subject: "JavaScript",
          subjectIcon: "javascript-img.svg",
          helpInfo: "Virkar ekki",
          teacherName: "Ellert Smári",
          teacherAvatar: "teacher-avatar.svg",
          studentName: "Æsa",
          studentAvatar: "student-avatar.svg",
          time: 5
        }
      ]
    };
  },
  computed: {},
  methods: {
    getImgUrl(pic) {
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
    getAccess() {
      this.isTeacher = this.teacherIs;
    },
    totalTime() {}
  },
  mounted() {
    // this.getAccess();
  }
};
</script>


<style lang="scss" >
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
