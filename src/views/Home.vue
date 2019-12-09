<template>
  <div class="container" id="home">
    <div class="user-greeting">
      <h1>Góðan daginn, {{logedUserInfo.name}}</h1>
      <img :src="getImgUrl(logedUserInfo.avatar)" alt="Notandi" />
      <!-- <hr /> -->
      <!-- <h3>{{isTeacher}}</h3> -->
    </div>
    <WaitingList :isTeacher="isTeacher" />
    <Interviews :isTeacher="isTeacher" />
  </div>
</template>

<script>
// @ is an alias to /src
import WaitingList from "@/components/WaitingList.vue";
import Interviews from "@/components/Interviews.vue";

export default {
  name: "Home",
  props: ["logedUserInfo"],
  components: {
    WaitingList,
    Interviews
  },
  data() {
    return {
      isTeacher: false
    };
  },
  methods: {
    getImgUrl(pic) {
      return require("../assets/" + pic);
    },
    getAccess() {
      if (this.logedUserInfo.teacher === true) {
        this.isTeacher = true;
      }
    }
  },
  mounted() {
    this.getAccess(this.logedUserInfo);
    console.log();
  }
};
</script>

<style lang="scss" >
.user-greeting {
  margin-bottom: 56px;
  @include flex(row, flex-start, center);
  h1 {
    font-size: 1.5rem;
    color: $navy-blue;
    text-align: left;
    font-weight: 700;
  }
  img {
    height: 41px;
    width: 41px;
    margin-left: 8px;
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  .user-greeting {
    padding: 8px 45px 64px;
  }
}
</style>
