import AllWaitingList from '@/components/sections/AllWaitingList';
<template>
  <div>
    <div id="open-wait" class="modal-window">
      <div>
        <a href="#Close" title="Close" class="modal-close">X</a>
        <form action @submit.prevent="onSubmit">
          <h1>Þarftu hjálp?</h1>
          <div class="row">
            <div class="col-75">
              <select id="subjectName" name="subjectName" v-model="form.subject" required>
                <option value="HTML/CSS">HTML/CSS</option>
                <option value="JavaScript">JavaScript</option>
                <option value="Hönnun">Hönnun</option>
                <option value="Vefþróun">Vefþróun</option>
              </select>
            </div>
          </div>
          <div class="row">
            <div class="col-75">
              <select id="teachers" name="teachers" v-model="form.teacherName" required>
                <option value="Smári">Smári</option>
                <option value="Pedro">Pedro</option>
                <option value="Jonathan">Jonathan</option>
              </select>
            </div>
          </div>
          <div class="row">
            <div class="col-75">
              <textarea
                id="info"
                name="info"
                placeholder="Nánari lýsing"
                style="height:200px"
                draggable="false"
                v-model="form.helpInfo"
                required
              ></textarea>
            </div>
          </div>
          <div class="row">
            <input type="submit" value="Staðfesta" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
    onSubmit() {
      let addHelp = {
        subject: this.subject,
        teacherName: this.teacherName,
        helpInfo: this.helpInfo
      };
      this.$emit("help-submitted", addHelp);
      (this.subject = ""), (this.teacherName = ""), (this.helpInfo = "");
      // Höndla input errors, sjá vue mastery video.
    }
  }
};
</script>


<style lang="scss" scope>
form {
  h1 {
    font-size: 24px;
    line-height: 34px;
    color: $navy-blue;
    font-weight: bold;
    text-align: left;
  }
}
input[type="text"],
select,
textarea {
  background-color: $light-grey;
  border-radius: 5px;
  color: black;
  border: none;
  margin: 0.5rem;
  width: 100%;
  padding: 1rem;
}
// textarea {
//   overflow: scroll;
//   resize: none;
// }

input[type="submit"] {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
}

input[type="submit"]:hover {
  background-color: #45a049;
}

.col-25 {
  float: left;
  width: 25%;
  margin-top: 6px;
}

.col-75 {
  float: left;
  width: 75%;
  margin-top: 6px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .col-25,
  .col-75,
  input[type="submit"] {
    width: 100%;
    margin-top: 0;
  }
}

// ********** MEDIA QUERIES **********

// *** MOBILE SIZE ***
@media only screen and (max-width: 900px) {
}
// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
}
</style>
