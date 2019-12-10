<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal" role="dialog">
        <form action @submit.prevent="onSubmit">
          <div class="modal-top">
            <h1>Þarftu hjálp?</h1>
            <a class="modal-close" @click="close" title="Loka">X</a>
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
            <select id="teachers" name="teachers" v-model="form.teacherName" required>
              <option value disabled selected hidden>Veldu kennara</option>
              <option value="Jonathan">Jonathan</option>
              <option value="Jónína">Jónína</option>
              <option value="Pedro">Pedro</option>
              <option value="Smári">Smári</option>
            </select>
          </div>
          <div class="form-element">
            <textarea
              id="info"
              name="info"
              placeholder="Nánari lýsing"
              draggable="false"
              v-model="form.helpInfo"
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
        subject: "",
        teacherName: "",
        helpInfo: ""
      }
    };
  },
  methods: {
    close() {
      this.$emit("close");
    },
    onSubmit() {
      let addHelp = {
        subject: this.form.subject,
        teacherName: this.form.teacherName,
        helpInfo: this.form.helpInfo,
        studentName: this.logedUserInfo.name,
        studentAvatar: this.logedUserInfo.avatar,
        teacherAvatar: "jonina-avatar.svg",
        time: 5
      };
      this.$emit("help-submitted", addHelp);
      this.$emit("close");
      (this.form.subject = ""),
        (this.form.teacherName = ""),
        (this.form.helpInfo = "");
    }
  }
};
</script>

<style lang="scss" >
</style>
