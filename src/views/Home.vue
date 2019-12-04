<template>
  <div class="container">
    <div class="user-greeting">
      <h1>Góðan daginn, Ósk</h1>
    </div>
    <WaitingList />
    <Interviews />
    <ModalHelpRequest />
  </div>
</template>

<script>
// @ is an alias to /src
import WaitingList from "@/components/WaitingList.vue";
import Interviews from "@/components/Interviews.vue";
import ModalHelpRequest from "@/components/modals/HelpRequest.vue";

export default {
  name: "home",
  components: {
    WaitingList,
    Interviews,
    ModalHelpRequest
  },
  data() {
    return {
      teacher: false
    };
  },
  computed: {
    testing() {
      console.log("Hæj frá Home.vue");
    }
  },
  mounted() {
    console.log("Hæjjjjaaaaa frá Home.vue");
  }
};
</script>

<style lang="scss" scope>
.user-greeting {
  padding: 40px 0px;
  h1 {
    font-size: 1.5rem;
    color: $navy-blue;
    text-align: left;
    font-weight: bold;
  }
}

@media only screen and (min-width: 900px) {
  .user-greeting {
    padding: 56px 45px 64px;
  }
}
</style>
