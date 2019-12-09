<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal" role="dialog">
        <form action @submit.prevent="onSubmit">
          <div class="modal-top">
            <h1>Nýtt viðtal</h1>
            <a class="modal-close" @click="close" title="Loka">X</a>
          </div>
          <div class="form-element">
            <select id="classGroup" name="classGroup" v-model="form.group" required>
              <option value disabled selected hidden class="disabled">Hópur</option>
              <option value="Hópur 3">Hópur 3</option>
              <option value="Hópur 4">Hópur 4</option>
            </select>
          </div>
          <div class="form-element">
            <select id="subjectName" name="subjectName" v-model="form.subject" required>
              <option value disabled selected hidden class="disabled">Veldu áfanga</option>
              <option value="HTML/CSS">HTML/CSS</option>
              <option value="JavaScript">JavaScript</option>
              <option value="Hönnun">Hönnun</option>
              <option value="Vefþróun">Vefþróun</option>
            </select>
          </div>
          <div class="form-element">
            <input
              type="number"
              min="0"
              max="99"
              maxlength="2"
              v-model="form.value"
              placeholder="Vægi %"
              required
            />
          </div>
          <div class="form-element">
            <input
              type="date"
              id="interviewDay"
              name="interviewDay"
              value="01-Dec-2019"
              v-model="form.day"
              required
            />
          </div>
          <div class="form-element-time">
            <h2>Veldu tíma sem eru í boði</h2>
            <div class="time-holder" id="interviewTime" name="interviewTime">
              <div class="time">
                <input type="checkbox" id="9" value="09:00" v-model="form.time" />
                <label for="9">09:00</label>
              </div>
              <div class="time">
                <input type="checkbox" id="930" value="09:30" v-model="form.time" />
                <label for="930">09:30</label>
              </div>
              <div class="time">
                <input type="checkbox" id="10" value="10:00" v-model="form.time" />
                <label for="10">10:00</label>
              </div>
              <div class="time">
                <input type="checkbox" id="1030" value="10:30" v-model="form.time" />
                <label for="1030">10:30</label>
              </div>
              <div class="time">
                <input type="checkbox" id="11" value="11:00" v-model="form.time" />
                <label for="11">11:00</label>
              </div>
            </div>
          </div>
          <div class="form-element">
            <textarea
              id="info"
              name="info"
              placeholder="Nánari lýsing"
              draggable="false"
              v-model="form.interviewInfo"
              required
            ></textarea>
          </div>
          <div class="btn-holder-modal">
            <div class="btn-confirm-md">
              <input type="submit" value="Staðfesta" />
            </div>
          </div>
        </form>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "ModalAddHelp",
  props: {
    logedUserInfo: Object
  },
  data() {
    return {
      form: {
        group: "",
        subject: "",
        value: "",
        day: "",
        time: [],
        interviewInfo: ""
      }
    };
  },
  methods: {
    close() {
      this.$emit("close");
    },
    onSubmit() {
      let addInterview = {
        group: this.form.group,
        subject: this.form.subject,
        value: this.form.value,
        date: this.form.day,
        time: this.form.time,
        info: this.form.interviewInfo,
        teacherName: this.logedUserInfo.name,
        teacherAvatar: this.logedUserInfo.avatar,
        subjectIcon: "javascript-img.svg"
      };
      this.$emit("interview-submitted", addInterview);
      this.$emit("close");
      (this.form.group = ""),
        (this.form.subject = ""),
        (this.form.value = ""),
        (this.form.day = ""),
        (this.form.time = ""),
        (this.form.interviewInfo = "");
      // Höndla input errors, sjá vue mastery video.
    }
  }
};
</script>


<style lang="scss" >
// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}
// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
